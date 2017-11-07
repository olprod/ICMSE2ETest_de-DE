---
title: Richtlinie CSP
description: Richtlinie CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4F3A1134-D401-44FC-A583-6EDD3070BA4F
ms.openlocfilehash: 41d675e8c01fb1ef6e297533fd0c736279e25fdc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="policy-csp"></a>Richtlinie CSP

Der Richtlinie Konfiguration-Dienstanbieter kann Unternehmen zum Konfigurieren von Richtlinien auf Windows 10. Verwenden Sie diese Konfiguration-Dienstanbieter, um alle Unternehmensrichtlinien konfigurieren.

Der Richtlinie Konfigurationsdienstanbieter weist die folgenden Unterkategorien:

-   *AreaName* – behandelt die Richtlinie Konfiguration Anforderung vom Server.
-   *AreaName* – stellt einen schreibgeschützten Pfad zur Richtlinien, die auf dem Gerät erzwungen.

Das folgende Diagramm zeigt den Richtlinie Konfigurationsdienstanbieter im Strukturformat von Open Allianz Verwaltung mobiler Geräte (OMA DM) sowohl OMA-Clientbereitstellung verwendet.

![Richtlinie Csp Diagramm](images/provisioning-csp-policy.png)


<a href="" id="--vendor-msft-policy"></a>**./Vendor/MSFT/Policy**  
<p style="margin-left: 20px">Der Stammknoten für die Richtlinie Konfiguration-Dienstanbieter.

<p style="margin-left: 20px">Unterstützte Vorgang ist Get.

<a href="" id="policy-config"></a>**Richtlinie/Config**  
<p style="margin-left: 20px">Der Knoten für die Gruppierung aller Richtlinien, die durch eine Quelle konfiguriert. Die Konfigurationsquelle kann mithilfe dieser Pfad Richtlinienwerte festlegen und Abfragen später einen beliebigen Richtlinienwert, die sie zuvor festgelegt. Eine Richtlinie kann von mehreren Konfigurationsquellen konfiguriert werden. Wenn eine Konfigurationsquelle möchte das Ergebnis der Konfliktbehebung Abfragen (z. B., wenn Exchange und MDM beide versuchen, ein Wert festgelegt), kann die Konfigurationsquelle den Richtlinie/Ergebnis Pfad verwenden, um den resultierenden Wert abzurufen.

<p style="margin-left: 20px">Unterstützte Vorgang ist Get.

<a href="" id="policy-config-areaname"></a>**Richtlinie/Config / ***_AreaName_**  
<p style="margin-left: 20px">Der Bereichsgruppe, die durch eine einzelne Technologie für einen einzelnen Anbieter konfiguriert werden kann. Nachdem hinzugefügt, können Sie den Wert nicht ändern.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Add, Get und löschen.

<a href="" id="policy-config-areaname-policyname"></a>**Richtlinie/Config / ***_AreaName/PolicyName_**  
<p style="margin-left: 20px">Gibt das Name/Wert-Paar in der Richtlinie verwendet.

<p style="margin-left: 20px">Die folgende Liste enthält einige Tipps, die Sie beim Konfigurieren von Richtlinien unterstützen:

-   Trennen Sie die Werte durch die Unicode-Teilzeichenfolge &\#xF000; in der XML-Datei.

> **Hinweis**  Eine Abfrage aus einer anderen Anrufer kann einen anderen Wert bereitstellen, da jeder Anrufer unterschiedliche Werte für eine benannte Richtlinie haben kann.

-   Umschließen Sie diese Richtlinie mit dem Befehl unteilbare SyncML so, dass die Richtlinieneinstellungen als eine einzelne Transaktion behandelt werden.
-   Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.
-   Werttyp ist Zeichenfolge.

<a href="" id="policy-result"></a>**Richtlinie/Ergebnis**  
<p style="margin-left: 20px">Gruppiert die ausgewerteten Richtlinien von allen Anbietern, die konfiguriert werden können.

<p style="margin-left: 20px">Unterstützte Vorgang ist Get.

<a href="" id="policy-result-areaname"></a>**Richtlinie/Ergebnis / ***_AreaName_**  
<p style="margin-left: 20px">Der Bereichsgruppe, die durch eine einzelne Technologie unabhängig von der Anbieter konfiguriert werden kann.

<p style="margin-left: 20px">Unterstützte Vorgang ist Get.

<a href="" id="policy-result-areaname-policyname"></a>**Richtlinie/Ergebnis / ***_AreaName/PolicyName_**  
<p style="margin-left: 20px">Gibt das Name/Wert-Paar in der Richtlinie verwendet.

<p style="margin-left: 20px">Unterstützte Vorgang ist Get.

## <a name="policy-tables"></a>**Gruppenrichtlinien-Tabellen**

Einige Richtlinien werden nur in entweder Windows-10 für Desktop oder Windows 10 Mobile unterstützt. Darüber hinaus können einige Richtlinien auch eine entsprechende Gruppenrichtlinie. In den folgenden Tabellen sind diese Informationen:

-   [Tabelle von Richtlinien für Windows 10](#mainpolicytable) : Listet alle Richtlinien für jede SKU in Windows 10. Diese Notizen auch Richtlinien, die mithilfe von Exchange Active Sync (EAS) festgelegt werden können.
-   [Von Windows Hologramm Enterprise unterstützt Richtlinien](#hololenspolicies) - zeigt die Richtlinien, die in Windows 10 Hologramm Unternehmen unterstützt werden.
-   [Richtlinien von Microsoft Surface Hub unterstützt](#surfacehubpolicies) – Listet die Richtlinien, die von Microsoft Surface Hub unterstützt werden.

## <a name="a-href-idmainpolicytableatable-of-policies-for-windows-10"></a><a href="" id="mainpolicytable"></a>Tabelle der Richtlinien für Windows 10

> **Wichtig**  Um die Tabelle horizontal zu navigieren, klicken Sie auf die Tabelle und mithilfe der linken und rechten Bildlaufleiste auf der Tastatur oder mithilfe der Bildlaufleiste am unteren Rand der Tabelle.

<table>
<tr>
<th>Bereichsnamen / Name der Richtlinie</th>
<th>Unterstützt in – Startseite</th>
<th>Unterstützt in Pro</th>
<th>Unterstützt in Unternehmen</th>
<th>In der Bildung unterstützt</th>
<th>In Mobile unterstützt</th>
<th>Unterstützt in mobilen Enterprise</th>
<th>Unterstützt in IoT Core</th>
<th>
       Kann mit Exchange Active Sync (EAS) festgelegt werden</th>
</tr>
<tr>
<td style="vertical-align:top"><a href="#abovelock-allowactioncenternotifications">AboveLock/AllowActionCenterNotifications</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#abovelock-allowcortanaabovelock">AboveLock/AllowCortanaAboveLock</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*
      <p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*
      <p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*
      <p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*
      <p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*
      <p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#abovelock-allowtoasts">AboveLock/AllowToasts</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#accounts-allowaddingnonmicrosoftaccountsmanually">Konten/AllowAddingNonMicrosoftAccountsManually</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#accounts-allowmicrosoftaccountconnection">Konten/AllowMicrosoftAccountConnection</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#accounts-domainnamesforemailsync">Konten/DomainNamesForEmailSync</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#applicationmanagement-allowalltrustedapps">ApplicationManagement/AllowAllTrustedApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#applicationmanagement-allowappstoreautoupdate">ApplicationManagement/AllowAppStoreAutoUpdate</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#applicationmanagement-allowdeveloperunlock">ApplicationManagement/AllowDeveloperUnlock</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#applicationmanagement-allowgamedvr">ApplicationManagement/AllowGameDVR</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#applicationmanagement-allowshareduserappdata">ApplicationManagement/AllowSharedUserAppData</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#applicationmanagement-allowstore">ApplicationManagement/AllowStore</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#applicationmanagement-applicationrestrictions">ApplicationManagement/ApplicationRestrictions</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#applicationmanagement-disablestoreoriginatedapps">ApplicationManagement/DisableStoreOriginatedApps</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#applicationmanagement-requireprivatestoreonly">ApplicationManagement/RequirePrivateStoreOnly</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#applicationmanagement-restrictappdatatosystemvolume">ApplicationManagement/RestrictAppDataToSystemVolume</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#applicationmanagement-restrictapptosystemvolume">ApplicationManagement/RestrictAppToSystemVolume</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#authentication-alloweapcertsso">Authentifizierung/AllowEAPCertSSO</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#authentication-allowfastreconnect">Authentifizierung/AllowFastReconnect</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#authentication-allowsecondaryauthenticationdevice">Authentifizierung/AllowSecondaryAuthenticationDevice</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#bitlocker-encryptionmethod">BitLocker/EncryptionMethod</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#bluetooth-allowadvertising">Bluetooth/AllowAdvertising</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#bluetooth-allowdiscoverablemode">Bluetooth/AllowDiscoverableMode</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#bluetooth-allowprepairing">Bluetooth/AllowPrepairing</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#bluetooth-localdevicename">Bluetooth/LocalDeviceName</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#bluetooth-servicesallowedlist">Bluetooth/ServicesAllowedList</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#browser-allowautofill">Browser/AllowAutofill</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#browser-allowbrowser">Browser/AllowBrowser</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#browser-allowcookies">Browser/AllowCookies</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"></td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#browser-allowdevelopertools">Browser/AllowDeveloperTools</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#browser-allowdonottrack">Browser/AllowDoNotTrack</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#browser-allowextensions">Browser/AllowExtensions</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#browser-allowinprivate">Browser/AllowInPrivate</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#browser-allowpasswordmanager">Browser/AllowPasswordManager</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#browser-allowpopups">Browser/AllowPopups</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#browser-allowsearchsuggestionsinaddressbar">Browser/AllowSearchSuggestionsinAddressBar</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#browser-allowsmartscreen">Browser/AllowSmartScreen</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#browser-enterprisemodesitelist">Browser/EnterpriseModeSiteList</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#browser-firstrunurl">Browser/FirstRunURL</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#browser-homepages">Browser/Homepages</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#browser-preventaccesstoaboutflagsinmicrosoftedge">Browser/PreventAccessToAboutFlagsInMicrosoftEdge</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#browser-preventsmartscreenpromptoverride">Browser/PreventSmartScreenPromptOverride</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#browser-preventsmartscreenpromptoverrideforfiles">Browser/PreventSmartScreenPromptOverrideForFiles</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#browser-preventusinglocalhostipaddressforwebrtc">Browser/PreventUsingLocalHostIPAddressForWebRTC</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#browser-sendintranettraffictointernetexplorer">Browser/SendIntranetTraffictoInternetExplorer</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#browser-showmessagewhenopeningsitesininternetexplorer">Browser/ShowMessageWhenOpeningSitesInInternetExplorer</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#camera-allowcamera">Kamera/AllowCamera</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#connectivity-allowbluetooth">Konnektivität/AllowBluetooth</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#connectivity-allowcellulardata">Konnektivität/AllowCellularData</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#connectivity-allowcellulardataroaming">Konnektivität/AllowCellularDataRoaming</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#connectivity-allownfc">Konnektivität/AllowNFC</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#connectivity-allowusbconnection">Konnektivität/AllowUSBConnection</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#connectivity-allowvpnovercellular">Konnektivität/AllowVPNOverCellular</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#connectivity-allowvpnroamingovercellular">Konnektivität/AllowVPNRoamingOverCellular</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#cryptography-allowfipsalgorithmpolicy">Kryptografie/AllowFipsAlgorithmPolicy</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#cryptography-tlsciphersuites">Kryptografie/TLSCipherSuites</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#dataprotection-allowdirectmemoryaccess">DataProtection/AllowDirectMemoryAccess</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#dataprotection-legacyselectivewipeid">DataProtection/LegacySelectiveWipeID</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-allowarchivescanning">Defender/AllowArchiveScanning</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-allowbehaviormonitoring">Defender/AllowBehaviorMonitoring</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-allowcloudprotection">Defender/AllowCloudProtection</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-allowemailscanning">Defender/AllowEmailScanning</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-allowfullscanonmappednetworkdrives">Defender/AllowFullScanOnMappedNetworkDrives</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-allowfullscanremovabledrivescanning">Defender/AllowFullScanRemovableDriveScanning</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-allowintrusionpreventionsystem">Defender/AllowIntrusionPreventionSystem</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-allowioavprotection">Defender/AllowIOAVProtection</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-allowonaccessprotection">Defender/AllowOnAccessProtection</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-allowrealtimemonitoring">Defender/AllowRealtimeMonitoring</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-allowscanningnetworkfiles">Defender/AllowScanningNetworkFiles</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-allowscriptscanning">Defender/AllowScriptScanning</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-allowuseruiaccess">Defender/AllowUserUIAccess</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-avgcpuloadfactor">Defender/AVGCPULoadFactor</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-daystoretaincleanedmalware">Defender/DaysToRetainCleanedMalware</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-excludedextensions">Defender/ExcludedExtensions</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-excludedpaths">Defender/ExcludedPaths</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-excludedprocesses">Defender/ExcludedProcesses</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-puaprotection">Defender/PUAProtection</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-realtimescandirection">Defender/RealTimeScanDirection</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-scanparameter">Defender/ScanParameter</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-schedulequickscantime">Defender/ScheduleQuickScanTime</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-schedulescanday">Defender/ScheduleScanDay</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-schedulescantime">Defender/ScheduleScanTime</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-signatureupdateinterval">Defender/SignatureUpdateInterval</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-submitsamplesconsent">Defender/SubmitSamplesConsent</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#defender-threatseveritydefaultaction">Defender/ThreatSeverityDefaultAction</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#deliveryoptimization-doabsolutemaxcachesize">DeliveryOptimization/DOAbsoluteMaxCacheSize</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#deliveryoptimization-dodownloadmode">DeliveryOptimization/DODownloadMode</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#deliveryoptimization-dogroupid">DeliveryOptimization/DOGroupID</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#deliveryoptimization-domaxcacheage">DeliveryOptimization/DOMaxCacheAge</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#deliveryoptimization-domaxcachesize">DeliveryOptimization/DOMaxCacheSize</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#deliveryoptimization-domaxdownloadbandwidth">DeliveryOptimization/DOMaxDownloadBandwidth</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#deliveryoptimization-domaxuploadbandwidth">DeliveryOptimization/DOMaxUploadBandwidth</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#deliveryoptimization-dominbackgroundqos">DeliveryOptimization/DOMinBackgroundQos</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#deliveryoptimization-domodifycachedrive">DeliveryOptimization/DOModifyCacheDrive</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#deliveryoptimization-domonthlyuploaddatacap">DeliveryOptimization/DOMonthlyUploadDataCap</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#deliveryoptimization-dopercentagemaxdownloadbandwidth">DeliveryOptimization/DOPercentageMaxDownloadBandwidth</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#devicelock-allowidlereturnwithoutpassword">DeviceLock/AllowIdleReturnWithoutPassword</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#devicelock-allowscreentimeoutwhilelockeduserconfig">DeviceLock/AllowScreenTimeoutWhileLockedUserConfig</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#devicelock-allowsimpledevicepassword">DeviceLock/AllowSimpleDevicePassword</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#devicelock-alphanumericdevicepasswordrequired">DeviceLock/AlphanumericDevicePasswordRequired</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#devicelock-devicepasswordenabled">DeviceLock/DevicePasswordEnabled</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#devicelock-devicepasswordexpiration">DeviceLock/DevicePasswordExpiration</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#devicelock-devicepasswordhistory">DeviceLock/DevicePasswordHistory</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#devicelock-enforcelockscreenandlogonimage">DeviceLock/EnforceLockScreenAndLogonImage</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#devicelock-enforcelockscreenprovider">DeviceLock/EnforceLockScreenProvider</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#devicelock-maxdevicepasswordfailedattempts">DeviceLock/MaxDevicePasswordFailedAttempts</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#devicelock-maxinactivitytimedevicelock">DeviceLock/MaxInactivityTimeDeviceLock</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#devicelock-mindevicepasswordcomplexcharacters">DeviceLock/MinDevicePasswordComplexCharacters</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#devicelock-screentimeoutwhilelocked">DeviceLock/ScreenTimeoutWhileLocked</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"></td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#devicelock-mindevicepasswordlength">DeviceLock/MinDevicePasswordLength</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#experience-allowcopypaste">Erfahrung/AllowCopyPaste</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#experience-allowcortana">Erfahrung/AllowCortana</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#experience-allowdevicediscovery">Erfahrung/AllowDeviceDiscovery</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#experience-allowmanualmdmunenrollment">Erfahrung/AllowManualMDMUnenrollment</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#experience-allowscreencapture">Erfahrung/AllowScreenCapture</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#experience-allowsimerrordialogpromptwhennosim">Erfahrung/AllowSIMErrorDialogPromptWhenNoSIM</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#experience-allowsyncmysettings">Erfahrung/AllowSyncMySettings</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#experience-allowtaskswitcher">Erfahrung/AllowTaskSwitcher</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#experience-allowthirdpartysuggestionsinwindowsspotlight">Erfahrung/AllowThirdPartySuggestionsInWindowsSpotlight</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#experience-allowvoicerecording">Erfahrung/AllowVoiceRecording</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#experience-allowwindowsconsumerfeatures">Erfahrung/AllowWindowsConsumerFeatures</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#experience-allowwindowsspotlight">Erfahrung/AllowWindowsSpotlight</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#experience-allowwindowstips">Erfahrung/AllowWindowsTips</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#experience-configurewindowsspotlightonlockscreen">Erfahrung/ConfigureWindowsSpotlightOnLockScreen</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#experience-donotshowfeedbacknotifications">Erfahrung/DoNotShowFeedbackNotifications</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#licensing-allowwindowsentitlementreactivation">Lizenzierung/AllowWindowsEntitlementReactivation</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#licensing-disallowkmsclientonlineavsvalidation">Lizenzierung/DisallowKMSClientOnlineAVSValidation</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#lockdown-allowedgeswipe">Sperren/AllowEdgeSwipe</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#maps-enableofflinemapsautoupdate">Karten/EnableOfflineMapsAutoUpdate</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#maps-allowofflinemapsdownloadovermeteredconnection">Karten/AllowOfflineMapsDownloadOverMeteredConnection</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#messaging-allowmessagesync">Messaging/AllowMessageSync</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#networkisolation-enterprisecloudresources">NetworkIsolation/EnterpriseCloudResources</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#networkisolation-enterpriseinternalproxyservers">NetworkIsolation/EnterpriseInternalProxyServers</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#networkisolation-enterpriseiprange">NetworkIsolation/EnterpriseIPRange</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#networkisolation-enterpriseiprangesareauthoritative">NetworkIsolation/EnterpriseIPRangesAreAuthoritative</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#networkisolation-enterprisenetworkdomainnames">NetworkIsolation/EnterpriseNetworkDomainNames</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#networkisolation-enterpriseproxyservers">NetworkIsolation/EnterpriseProxyServers</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#networkisolation-enterpriseproxyserversareauthoritative">NetworkIsolation/EnterpriseProxyServersAreAuthoritative</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#networkisolation-neutralresources">NetworkIsolation/NeutralResources</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#notifications-disallownotificationmirroring">Benachrichtigungen/DisallowNotificationMirroring</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-allowautoacceptpairingandprivacyconsentprompts">Datenschutz/AllowAutoAcceptPairingAndPrivacyConsentPrompts</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-allowinputpersonalization">Datenschutz/AllowInputPersonalization</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-disableadvertisingid">Datenschutz/DisableAdvertisingId</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessaccountinfo">Datenschutz/LetAppsAccessAccountInfo</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessaccountinfo-forceallowtheseapps">Datenschutz/LetAppsAccessAccountInfo_ForceAllowTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessaccountinfo-forcedenytheseapps">Datenschutz/LetAppsAccessAccountInfo_ForceDenyTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessaccountinfo-userincontroloftheseapps">Datenschutz/LetAppsAccessAccountInfo_UserInControlOfTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesscalendar">Datenschutz/LetAppsAccessCalendar</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesscalendar-forceallowtheseapps">Datenschutz/LetAppsAccessCalendar_ForceAllowTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesscalendar-forcedenytheseapps">Datenschutz/LetAppsAccessCalendar_ForceDenyTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesscalendar-userincontroloftheseapps">Datenschutz/LetAppsAccessCalendar_UserInControlOfTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesscallhistory">Datenschutz/LetAppsAccessCallHistory</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesscallhistory-forceallowtheseapps">Datenschutz/LetAppsAccessCallHistory_ForceAllowTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesscallhistory-forcedenytheseapps">Datenschutz/LetAppsAccessCallHistory_ForceDenyTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesscallhistory-userincontroloftheseapps">Datenschutz/LetAppsAccessCallHistory_UserInControlOfTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesscamera">Datenschutz/LetAppsAccessCamera</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesscamera-forceallowtheseapps">Datenschutz/LetAppsAccessCamera_ForceAllowTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesscamera-forcedenytheseapps">Datenschutz/LetAppsAccessCamera_ForceDenyTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesscamera-userincontroloftheseapps">Datenschutz/LetAppsAccessCamera_UserInControlOfTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesscontacts">Datenschutz/LetAppsAccessContacts</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesscontacts-forceallowtheseapps">Datenschutz/LetAppsAccessContacts_ForceAllowTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesscontacts-forcedenytheseapps">Datenschutz/LetAppsAccessContacts_ForceDenyTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesscontacts-userincontroloftheseapps">Datenschutz/LetAppsAccessContacts_UserInControlOfTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessemail">Datenschutz/LetAppsAccessEmail</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessemail-forceallowtheseapps">Datenschutz/LetAppsAccessEmail_ForceAllowTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessemail-forcedenytheseapps">Datenschutz/LetAppsAccessEmail_ForceDenyTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessemail-userincontroloftheseapps">Datenschutz/LetAppsAccessEmail_UserInControlOfTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesslocation">Datenschutz/LetAppsAccessLocation</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesslocation-forceallowtheseapps">Datenschutz/LetAppsAccessLocation_ForceAllowTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesslocation-forcedenytheseapps">Datenschutz/LetAppsAccessLocation_ForceDenyTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesslocation-userincontroloftheseapps">Datenschutz/LetAppsAccessLocation_UserInControlOfTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessmessaging">Datenschutz/LetAppsAccessMessaging</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessmessaging-forceallowtheseapps">Datenschutz/LetAppsAccessMessaging_ForceAllowTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessmessaging-forcedenytheseapps">Datenschutz/LetAppsAccessMessaging_ForceDenyTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessmessaging-userincontroloftheseapps">Datenschutz/LetAppsAccessMessaging_UserInControlOfTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessmicrophone">Datenschutz/LetAppsAccessMicrophone</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessmicrophone-forceallowtheseapps">Datenschutz/LetAppsAccessMicrophone_ForceAllowTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessmicrophone-forcedenytheseapps">Datenschutz/LetAppsAccessMicrophone_ForceDenyTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessmicrophone-userincontroloftheseapps">Datenschutz/LetAppsAccessMicrophone_UserInControlOfTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessmotion">Datenschutz/LetAppsAccessMotion</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessmotion-forceallowtheseapps">Datenschutz/LetAppsAccessMotion_ForceAllowTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessmotion-forcedenytheseapps">Datenschutz/LetAppsAccessMotion_ForceDenyTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessmotion-userincontroloftheseapps">Datenschutz/LetAppsAccessMotion_UserInControlOfTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessnotifications">Datenschutz/LetAppsAccessNotifications</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessnotifications-forceallowtheseapps">Datenschutz/LetAppsAccessNotifications_ForceAllowTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessnotifications-forcedenytheseapps">Datenschutz/LetAppsAccessNotifications_ForceDenyTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessnotifications-userincontroloftheseapps">Datenschutz/LetAppsAccessNotifications_UserInControlOfTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessphone">Datenschutz/LetAppsAccessPhone</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/></td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessphone-forceallowtheseapps">Datenschutz/LetAppsAccessPhone_ForceAllowTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessphone-forcedenytheseapps">Datenschutz/LetAppsAccessPhone_ForceDenyTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessphone-userincontroloftheseapps">Datenschutz/LetAppsAccessPhone_UserInControlOfTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessradios">Datenschutz/LetAppsAccessRadios</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessradios-forceallowtheseapps">Datenschutz/LetAppsAccessRadios_ForceAllowTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessradios-forcedenytheseapps">Datenschutz/LetAppsAccessRadios_ForceDenyTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccessradios-userincontroloftheseapps">Datenschutz/LetAppsAccessRadios_UserInControlOfTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesstrusteddevices">Datenschutz/LetAppsAccessTrustedDevices</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesstrusteddevices-forceallowtheseapps">Datenschutz/LetAppsAccessTrustedDevices_ForceAllowTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesstrusteddevices-forcedenytheseapps">Datenschutz/LetAppsAccessTrustedDevices_ForceDenyTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappsaccesstrusteddevices-userincontroloftheseapps">Datenschutz/LetAppsAccessTrustedDevices_UserInControlOfTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappssyncwithdevices">Datenschutz/LetAppsSyncWithDevices</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappssyncwithdevices-forceallowtheseapps">Datenschutz/LetAppsSyncWithDevices_ForceAllowTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappssyncwithdevices-forcedenytheseapps">Datenschutz/LetAppsSyncWithDevices_ForceDenyTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#privacy-letappssyncwithdevices-userincontroloftheseapps">Datenschutz/LetAppsSyncWithDevices_UserInControlOfTheseApps</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#search-allowindexingencryptedstoresoritems">Suchen/AllowIndexingEncryptedStoresOrItems</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#search-allowsearchtouselocation">Suchen/AllowSearchToUseLocation</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#search-allowusingdiacritics">Suchen/AllowUsingDiacritics</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#search-alwaysuseautolangdetection">Suchen/AlwaysUseAutoLangDetection</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#search-disablebackoff">Suchen/DisableBackoff</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#search-disableremovabledriveindexing">Suchen/DisableRemovableDriveIndexing</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#search-preventindexinglowdiskspacemb">Suchen/PreventIndexingLowDiskSpaceMB</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#search-preventremotequeries">Suchen/PreventRemoteQueries</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#search-safesearchpermissions">Suchen/SafeSearchPermissions</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#security-allowaddprovisioningpackage">Security/AllowAddProvisioningPackage</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#security-allowautomaticdeviceencryptionforazureadjoineddevices">Security/AllowAutomaticDeviceEncryptionForAzureADJoinedDevices</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#security-allowmanualrootcertificateinstallation">Security/AllowManualRootCertificateInstallation</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#security-allowremoveprovisioningpackage">Security/AllowRemoveProvisioningPackage</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#security-antitheftmode">Security/AntiTheftMode</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#security-allowautomaticdeviceencryptionforazureadjoineddevices">Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#security-requiredeviceencryption">Security/RequireDeviceEncryption</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#security-requireprovisioningpackagesignature">Security/RequireProvisioningPackageSignature</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#security-requireretrievehealthcertificateonboot">Security/RequireRetrieveHealthCertificateOnBoot</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#settings-allowautoplay">Einstellungen/AllowAutoPlay</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#settings-allowdatasense">Einstellungen/AllowDataSense</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#settings-allowdatetime">Einstellungen/AllowDateTime</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#settings-alloweditdevicename">Einstellungen/AllowEditDeviceName</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#settings-allowlanguage">Einstellungen/AllowLanguage</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#settings-allowpowersleep">Einstellungen/AllowPowerSleep</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#settings-allowregion">Einstellungen/AllowRegion</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#settings-allowsigninoptions">Einstellungen/AllowSignInOptions</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#settings-allowvpn">Einstellungen/AllowVPN</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#settings-allowworkplace">Einstellungen/AllowWorkplace</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#settings-allowyouraccount">Einstellungen/AllowYourAccount</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#speech-allowspeechmodelupdate">Spracherkennung/AllowSpeechModelUpdate</a></td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#start-forcestartsize">Start/ForceStartSize</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#start-startlayout">Start-/StartLayout</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#system-allowbuildpreview">System/AllowBuildPreview</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#system-allowembeddedmode">System/AllowEmbeddedMode</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"></td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#system-allowexperimentation">System/AllowExperimentation</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#system-allowlocation">System/AllowLocation</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#system-allowstoragecard">System/AllowStorageCard</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#system-allowtelemetry">System/AllowTelemetry</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#system-allowusertoresetphone">System/AllowUserToResetPhone</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#system-telemetryproxy">System/TelemetryProxy</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#textinput-allowimelogging">TextInput/AllowIMELogging</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#textinput-allowimenetworkaccess">TextInput/AllowIMENetworkAccess</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#textinput-allowinputpanel">TextInput/AllowInputPanel</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#textinput-allowjapaneseimesurrogatepaircharacters">TextInput/AllowJapaneseIMESurrogatePairCharacters</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#textinput-allowjapaneseivscharacters">TextInput/AllowJapaneseIVSCharacters</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#textinput-allowjapanesenonpublishingstandardglyph">TextInput/AllowJapaneseNonPublishingStandardGlyph</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#textinput-allowjapaneseuserdictionary">TextInput/AllowJapaneseUserDictionary</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#textinput-allowlanguagefeaturesuninstall">TextInput/AllowLanguageFeaturesUninstall</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#textinput-allowlinguisticdatacollection">TextInput/AllowLinguisticDataCollection</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#textinput-excludejapaneseimeexceptjis0208">TextInput/ExcludeJapaneseIMEExceptJIS0208</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#textinput-excludejapaneseimeexceptjis0208andeudc">TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#textinput-excludejapaneseimeexceptshiftjis">TextInput/ExcludeJapaneseIMEExceptShiftJIS</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#update-activehoursend">Update/ActiveHoursEnd</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#update-activehoursstart">Update/ActiveHoursStart</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#update-allowautoupdate">Update/AllowAutoUpdate</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#update-allowmuupdateservice">Update/AllowMUUpdateService</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#update-allownonmicrosoftsignedupdate">Update/AllowNonMicrosoftSignedUpdate</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#update-allowupdateservice">Update/AllowUpdateService</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#update-branchreadinesslevel">Update/BranchReadinessLevel</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#update-deferfeatureupdatesperiodindays">Update/DeferFeatureUpdatesPeriodInDays</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#update-deferqualityupdatesperiodindays">Update/DeferQualityUpdatesPeriodInDays</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#update-deferupdateperiod">Update/DeferUpdatePeriod</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#update-deferupgradeperiod">Update/DeferUpgradePeriod</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#update-excludewudriversinqualityupdate">Update/ExcludeWUDriversInQualityUpdate</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#update-pausedeferrals">Update/PauseDeferrals</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#update-pausefeatureupdates">Update/PauseFeatureUpdates</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#update-pausequalityupdates">Update/PauseQualityUpdates</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#update-requiredeferupgrade">Update/RequireDeferUpgrade</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#update-requireupdateapproval">Update/RequireUpdateApproval</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#update-scheduledinstallday">Update/ScheduledInstallDay</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#update-scheduledinstalltime">Update/ScheduledInstallTime</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#update-updateserviceurl">Update/UpdateServiceUrl</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#wifi-allowautoconnecttowifisensehotspots">WiFi/AllowAutoConnectToWiFiSenseHotspots</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#wifi-allowinternetsharing">WiFi/AllowInternetSharing</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#wifi-allowmanualwificonfiguration">WiFi/AllowManualWiFiConfiguration</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#wifi-allowwifi">WiFi/AllowWiFi</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#wifi-wlanscanmode">WiFi/WLANScanMode</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#windowsinkworkspace-allowwindowsinkworkspace">WindowsInkWorkspace/AllowWindowsInkWorkspace</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#windowsinkworkspace-allowsuggestedappsinwindowsinkworkspace">WindowsInkWorkspace/AllowSuggestedAppsInWindowsInkWorkspace</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#wirelessdisplay-allowprojectiontopc">WirelessDisplay/AllowProjectionToPC</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
<tr>
<td style="vertical-align:top"><a href="#wirelessdisplay-requirepinforpairing">WirelessDisplay/RequirePinForPairing</a></td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Home (Homepage) </p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Pro</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CheckMark.png" alt="check mark"/>*<p>Education</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>Mobile Enterprise</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>IoT Core</p>
</td>
<td style="vertical-align:top"><img src="images/CrossMark.png" alt="cross mark"/><p>EAS</p>
</td>
</tr>
</table>

 

Fußnote:

-   \*-In Windows 10, Version 1607 hinzugefügt.

## <a name="a-href-idhololenspoliciesapolicies-supported-by-windows-holographic-enterprise"></a><a href="" id="hololenspolicies"></a>Richtlinien, die von Windows Hologramm Enterprise unterstützt

-   [Konten/AllowMicrosoftAccountConnection](#accounts-allowmicrosoftaccountconnection)
-   [ApplicationManagement/AllowAllTrustedApps](#applicationmanagement-allowalltrustedapps)
-   [ApplicationManagement/AllowAppStoreAutoUpdate](#applicationmanagement-allowappstoreautoupdate)
-   [ApplicationManagement/AllowDeveloperUnlock](#applicationmanagement-allowdeveloperunlock)
-   [Authentifizierung/AllowFastReconnect](#authentication-allowfastreconnect)
-   [Bluetooth/AllowAdvertising](#bluetooth-allowadvertising)
-   [Bluetooth/AllowDiscoverableMode](#bluetooth-allowdiscoverablemode)
-   [Bluetooth/LocalDeviceName](#bluetooth-localdevicename)
-   [Browser/AllowCookies](#browser-allowcookies)
-   [Browser/AllowDoNotTrack](#browser-allowdonottrack)
-   [Browser/AllowPasswordManager](#browser-allowpasswordmanager)
-   [Browser/AllowPopups](#browser-allowpopups)
-   [Browser/AllowSearchSuggestionsinAddressBar](#browser-allowsearchsuggestionsinaddressbar)
-   [Browser/AllowSmartScreen](#browser-allowsmartscreen)
-   [Konnektivität/AllowBluetooth](#connectivity-allowbluetooth)
-   [DeviceLock/AllowIdleReturnWithoutPassword](#devicelock-allowidlereturnwithoutpassword)
-   [DeviceLock/DevicePasswordEnabled](#devicelock-devicepasswordenabled)
-   [Erfahrung/AllowCortana](#experience-allowcortana)
-   [Erfahrung/AllowManualMDMUnenrollment](#experience-allowmanualmdmunenrollment)
-   [Datenschutz/AllowInputPersonalization](#privacy-allowinputpersonalization)
-   [Suchen/AllowSearchToUseLocation](#search-allowsearchtouselocation)
-   [Security/RequireDeviceEncryption](#security-requiredeviceencryption)
-   [Einstellungen/AllowDateTime](#settings-allowdatetime)
-   [Einstellungen/AllowVPN](#settings-allowvpn)
-   [System/AllowLocation](#system-allowlocation)
-   [System/AllowTelemetry](#system-allowtelemetry)
-   [Update/AllowAutoUpdate](#update-allowautoupdate)
-   [Update/AllowUpdateService](#update-allowupdateservice)
-   [Update/RequireDeferUpgrade](#update-requiredeferupgrade)
-   [Update/RequireUpdateApproval](#update-requireupdateapproval)
-   [Update/UpdateServiceUrl](#update-updateserviceurl)


## <a name="a-href-idsurfacehubpoliciesapolicies-supported-by-microsoft-surface-hub"></a><a href="" id="surfacehubpolicies"></a>Richtlinien von Microsoft Surface Hub unterstützt

-   [Bluetooth/AllowAdvertising](#bluetooth-allowadvertising)
-   [Bluetooth/AllowDiscoverableMode](#bluetooth-allowdiscoverablemode)
-   [Bluetooth/AllowPrepairing](#bluetooth-allowprepairing)
-   [Bluetooth/LocalDeviceName](#bluetooth-localdevicename)
-   [Bluetooth/ServicesAllowedList](#bluetooth-servicesallowedlist)
-   [Browser/Homepages](#browser-homepages)
-   [Browser/AllowCookies](#browser-allowcookies)
-   [Browser/AllowDeveloperTools](#browser-allowdevelopertools)
-   [Browser/AllowDoNotTrack](#browser-allowdonottrack)
-   [Browser/AllowPopups](#browser-allowpopups)
-   [Browser/AllowSearchSuggestionsinAddressBar](#browser-allowsearchsuggestionsinaddressbar)
-   [Browser/AllowSmartScreen](#browser-allowsmartscreen)
-   [Browser/PreventSmartScreenPromptOverride](#browser-preventsmartscreenpromptoverride)
-   [Browser/PreventSmartScreenPromptOverrideForFiles](#browser-preventsmartscreenpromptoverrideforfiles)
-   [Kamera/AllowCamera](#camera-allowcamera)
-   [Konnektivität/AllowBluetooth](#connectivity-allowbluetooth)
-   [Kryptografie/AllowFipsAlgorithmPolicy](#cryptography-allowfipsalgorithmpolicy)
-   [Kryptografie/TLSCipherSuites](#cryptography-tlsciphersuites)
-   [Defender/AllowArchiveScanning](#defender-allowarchivescanning)
-   [Defender/AllowBehaviorMonitoring](#defender-allowbehaviormonitoring)
-   [Defender/AllowCloudProtection](#defender-allowcloudprotection)
-   [Defender/AllowEmailScanning](#defender-allowemailscanning)
-   [Defender/AllowFullScanOnMappedNetworkDrives](#defender-allowfullscanonmappednetworkdrives)
-   [Defender/AllowFullScanRemovableDriveScanning](#defender-allowfullscanremovabledrivescanning)
-   [Defender/AllowIntrusionPreventionSystem](#defender-allowintrusionpreventionsystem)
-   [Defender/AllowIOAVProtection](#defender-allowioavprotection)
-   [Defender/AllowOnAccessProtection](#defender-allowonaccessprotection)
-   [Defender/AllowRealtimeMonitoring](#defender-allowrealtimemonitoring)
-   [Defender/AllowScanningNetworkFiles](#defender-allowscanningnetworkfiles)
-   [Defender/AllowScriptScanning](#defender-allowscriptscanning)
-   [Defender/AllowUserUIAccess](#defender-allowuseruiaccess)
-   [Defender/AVGCPULoadFactor](#defender-avgcpuloadfactor)
-   [Defender/DaysToRetainCleanedMalware](#defender-daystoretaincleanedmalware)
-   [Defender/ExcludedExtensions](#defender-excludedextensions)
-   [Defender/ExcludedPaths](#defender-excludedpaths)
-   [Defender/ExcludedProcesses](#defender-excludedprocesses)
-   [Defender/PUAProtection](#defender-puaprotection)
-   [Defender/RealTimeScanDirection](#defender-realtimescandirection)
-   [Defender/ScanParameter](#defender-scanparameter)
-   [Defender/ScheduleQuickScanTime](#defender-schedulequickscantime)
-   [Defender/ScheduleScanDay](#defender-schedulescanday)
-   [Defender/ScheduleScanTime](#defender-schedulescantime)
-   [Defender/SignatureUpdateInterval](#defender-signatureupdateinterval)
-   [Defender/SubmitSamplesConsent](#defender-submitsamplesconsent)
-   [Defender/ThreatSeverityDefaultAction](#defender-threatseveritydefaultaction)
-   [DeliveryOptimization/DOAbsoluteMaxCacheSize](#deliveryoptimization-doabsolutemaxcachesize)
-   [DeliveryOptimization/DODownloadMode](#deliveryoptimization-dodownloadmode)
-   [DeliveryOptimization/DOGroupID](#deliveryoptimization-dogroupid)
-   [DeliveryOptimization/DOMaxCacheAge](#deliveryoptimization-domaxcacheage)
-   [DeliveryOptimization/DOMaxCacheSize](#deliveryoptimization-domaxcachesize)
-   [DeliveryOptimization/DOMaxDownloadBandwidth](#deliveryoptimization-domaxdownloadbandwidth)
-   [DeliveryOptimization/DOMaxUploadBandwidth](#deliveryoptimization-domaxuploadbandwidth)
-   [DeliveryOptimization/DOMinBackgroundQos](#deliveryoptimization-dominbackgroundqos)
-   [DeliveryOptimization/DOModifyCacheDrive](#deliveryoptimization-domodifycachedrive)
-   [DeliveryOptimization/DOMonthlyUploadDataCap](#deliveryoptimization-domonthlyuploaddatacap)
-   [DeliveryOptimization/DOPercentageMaxDownloadBandwidth](#deliveryoptimization-dopercentagemaxdownloadbandwidth)
-   [Security/RequireProvisioningPackageSignature](#security-requireprovisioningpackagesignature)
-   [Security/RequireRetrieveHealthCertificateOnBoot](#security-requireretrievehealthcertificateonboot)
-   [System/AllowLocation](#system-allowlocation)
-   [System/AllowTelemetry](#system-allowtelemetry)
-   [TextInput/AllowIMELogging](#textinput-allowimelogging)
-   [TextInput/AllowIMENetworkAccess](#textinput-allowimenetworkaccess)
-   [TextInput/AllowInputPanel](#textinput-allowinputpanel)
-   [TextInput/AllowJapaneseIMESurrogatePairCharacters](#textinput-allowjapaneseimesurrogatepaircharacters)
-   [TextInput/AllowJapaneseIVSCharacters](#textinput-allowjapaneseivscharacters)
-   [TextInput/AllowJapaneseNonPublishingStandardGlyph](#textinput-allowjapanesenonpublishingstandardglyph)
-   [TextInput/AllowJapaneseUserDictionary](#textinput-allowjapaneseuserdictionary)
-   [TextInput/AllowLanguageFeaturesUninstall](#textinput-allowlanguagefeaturesuninstall)
-   [TextInput/AllowLinguisticDataCollection](#textinput-allowlinguisticdatacollection)
-   [TextInput/ExcludeJapaneseIMEExceptJIS0208](#textinput-excludejapaneseimeexceptjis0208)
-   [TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC](#textinput-excludejapaneseimeexceptjis0208andeudc)
-   [TextInput/ExcludeJapaneseIMEExceptShiftJIS](#textinput-excludejapaneseimeexceptshiftjis)
-   [Update/AllowAutoUpdate](#update-allowautoupdate)
-   [Update/AllowUpdateService](#update-allowupdateservice)
-   [Update/BranchReadinessLevel](#update-branchreadinesslevel)
-   [Update/DeferFeatureUpdatesPeriodInDays](#update-deferfeatureupdatesperiodindays)
-   [Update/DeferQualityUpdatesPeriodInDays](#update-deferqualityupdatesperiodindays)
-   [Update/PauseFeatureUpdates](#update-pausefeatureupdates)
-   [Update/PauseQualityUpdates](#update-pausequalityupdates)
-   [Update/UpdateServiceUrl](#update-updateserviceurl)


## <a name="a-href-idlist-of--areaname---policyname-alist-of-ltareanamegtltpolicynamegt"></a><a href="" id="list-of--areaname---policyname-"></a>Liste der &lt;AreaName&gt;/&lt;PolicyName&gt;

<a href="" id="abovelock-allowactioncenternotifications"></a>**AboveLock/AllowActionCenterNotifications**  
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Mobile erzwungen und im Windows-10 für Desktop nicht unterstützt.

<p style="margin-left: 20px">Gibt an, ob die Aktion Center-Benachrichtigungen über die Geräte Sperrbildschirm zulassen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="abovelock-allowcortanaabovelock"></a>**AboveLock/AllowCortanaAboveLock**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt an, ob der Benutzer interagieren kann mit Cortana per Sprache, während das System gesperrt ist. Wenn Sie aktivieren oder diese Einstellung nicht konfigurieren, kann der Benutzer interagieren mit Cortana per Sprache, während das System gesperrt ist. Wenn Sie diese Einstellung deaktivieren, müssen das System für den Benutzer zur Interaktion mit Cortana per Sprache aufgehoben werden.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="abovelock-allowtoasts"></a>**AboveLock/AllowToasts**  
<p style="margin-left: 20px">Gibt an, ob Benachrichtigungen über die Geräte Sperrbildschirm Toast zulassen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zulässig.
-   1 (Standard) – zulässig.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="accounts-allowaddingnonmicrosoftaccountsmanually"></a>**Konten/AllowAddingNonMicrosoftAccountsManually**  
<p style="margin-left: 20px">Gibt an, ob Benutzer berechtigt ist, nicht MSA e-Mail-Konten hinzufügen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

> **Hinweis**  Diese Richtlinie blockiert nur UI, UX-basierte Methoden zum Hinzufügen von Konten nicht von Microsoft. Auch wenn diese Richtlinie erzwungen wird, können Sie noch nicht MSA Konten mit dem [EMAIL2 CSP](email2-csp.md)bereitstellen.

<a href="" id="accounts-allowmicrosoftaccountconnection"></a>**Konten/AllowMicrosoftAccountConnection**  
<p style="margin-left: 20px">Gibt an, ob der Benutzer berechtigt ist, ein Konto MSA für verwandte ohne e-Mail-Verbindungsauthentifizierung und die Dienste zu verwenden.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="accounts-domainnamesforemailsync"></a>**Konten/DomainNamesForEmailSync**  
<p style="margin-left: 20px">Gibt eine Liste der Domänen, die für die Synchronisierung von e-Mail auf dem Gerät zulässig sind.

<p style="margin-left: 20px">Der Datentyp ist eine Zeichenfolge.

<p style="margin-left: 20px">Der Standardwert ist eine leere Zeichenfolge, wodurch alle e-Mail-Konten auf dem Gerät e-Mail synchronisieren. Andernfalls sollte die Zeichenfolge eine Pipe getrennte Liste der Domänen enthalten, die für die Synchronisierung von e-Mail auf dem Gerät zulässig sind. Beispielsweise "contoso.com|fabrikam.net|woodgrove.gov".

<a href="" id="applicationmanagement-allowalltrustedapps"></a>**ApplicationManagement/AllowAllTrustedApps**  
<p style="margin-left: 20px">Gibt an, ob nicht Windows Store-apps zulässig sind.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Explicit verweigern.
-   1 – explizit zulassen entsperren.
-   65535 (Standard) – nicht konfiguriert.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="applicationmanagement-allowappstoreautoupdate"></a>**ApplicationManagement/AllowAppStoreAutoUpdate**  
<p style="margin-left: 20px">Gibt an, ob die automatische Aktualisierung von Windows Store-Apps sind zulässig.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="applicationmanagement-allowdeveloperunlock"></a>**ApplicationManagement/AllowDeveloperUnlock**  
<p style="margin-left: 20px">Gibt an, ob Developer entsperren ist zulässig.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Explicit verweigern.
-   1 – explizit zulassen entsperren.
-   65535 (Standard) – nicht konfiguriert.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="applicationmanagement-allowgamedvr"></a>**ApplicationManagement/AllowGameDVR**   
> **Hinweis**  Die Richtlinie wird nur für Desktop in Windows 10 erzwungen.

<p style="margin-left: 20px">Gibt an, ob DVR und-Übertragung ist zulässig.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="applicationmanagement-allowshareduserappdata"></a>**ApplicationManagement/AllowSharedUserAppData**  
<p style="margin-left: 20px">Gibt an, ob mehrere Benutzer mit der gleichen app Daten freigegeben werden können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – nicht zulässig.
-   1 – zulässig.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="applicationmanagement-allowstore"></a>**ApplicationManagement/AllowStore**  
<p style="margin-left: 20px">Gibt an, ob die app-Store auf dem Gerät zulässig ist.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zulässig.
-   1 (Standard) – zulässig.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="applicationmanagement-applicationrestrictions"></a>**ApplicationManagement/ApplicationRestrictions**   
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Mobile erzwungen und im Windows-10 für Desktop nicht unterstützt. Verwenden Sie für desktop-Geräte stattdessen die [AppLocker CSP](applocker-csp.md) .

 
<p style="margin-left: 20px">Ein XML-Blob, der angibt, dass das Anwendung Einschränkungen Unternehmen auf das Gerät aufnehmen möchten. Möglicherweise eine app Zulassungsliste, app nicht zulassen, Liste, zulässigen Publisher-IDs und So weiter. Eine Liste der Windows-apps und Produkt-ID finden Sie unter [Posteingang-apps](applocker-csp.md#inboxappsandcomponents). Weitere Informationen zu den XML-CODE finden Sie unter der [ApplicationRestrictions XSD](applicationrestrictions-xsd.md).

> **Hinweis**  
>  Beim upgrade von Windows Phone 8.1 Geräte auf 10 Mobile Windows mit einer Liste der zulässigen apps abrufen einige apps für Windows Posteingang verursacht unerwartetes Verhalten blockiert. Um dieses Problem zu umgehen, müssen Sie den [Posteingang apps](applocker-csp.md#inboxappsandcomponents) einschließen, die Sie Ihrer Liste der zulässigen apps müssen.
>
> Hier finden zusätzliche Richtlinien für den Upgradevorgang:
>
>  -   Verwenden Sie Windows-10-Produkt-IDs für die apps in [Posteingang apps](applocker-csp.md#inboxappsandcomponents)aufgeführt.
>  -   Verwenden Sie den Namen der neuen Microsoft Publisher (PublisherName = "CN = Microsoft Corporation, O = Microsoft Corporation, L = Redmond, S Washington, C = = US") und eines vertrauenswürdigen Herausgebers = "CN = Microsoft Windows, O = Microsoft Corporation, L = Redmond, S Washington, C = = US" bei Verwendung die Publisher-Richtlinie. Windows Phone 8.1 Herausgeber kann nicht entfernt werden, wenn Sie es verwenden.
>  -   In der SyncML müssen Sie Kleinbuchstaben-Produkt-ID verwenden.
>  -   Führen Sie eine Product ID nicht doppelt Messaging und Skype Videofunktionen verwenden die gleichen Produkt-ID Duplikate führt zu einer Fehlermeldung.
>  -   Sie können nicht deaktivieren oder aktivieren **Kontakt Support** und **Feedback Windows** -apps mithilfe der ApplicationManagement/ApplicationRestrictions-Richtlinie, obwohl diese im [Posteingang apps](applocker-csp.md#inboxappsandcomponents)aufgeführt sind.


<p style="margin-left: 20px">Eine Anwendung, die ausgeführt wird, kann nicht sofort beendet werden.

<p style="margin-left: 20px">Werttyp ist chr.

<p style="margin-left: 20px">Wert Evaluation - Regel, die Informationen für PolicyManager ist nicht transparent. Es ist keine am meisten eingeschränkte Wert Bewertung. Sobald eine Änderung des Werts vorhanden ist, wird das Gerät analysiert den Knotenwert und erzwingt angegebene Richtlinien.

<a href="" id="applicationmanagement-disablestoreoriginatedapps"></a>**ApplicationManagement/DisableStoreOriginatedApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Boolescher Wert, der die Einführung von alle aus Windows Store-apps deaktiviert, die vorinstallierte stammt oder heruntergeladen wurden.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – Enable Starten von apps.
-   1 – deaktivieren Sie Einführung von apps.

<a href="" id="applicationmanagement-requireprivatestoreonly"></a>**ApplicationManagement/RequirePrivateStoreOnly**  
<p style="margin-left: 20px">Ermöglicht das Deaktivieren des Katalogs Verkaufsversion und können nur den privaten Speicher.

> **Wichtige**  
> Dieser Knoten muss über den folgenden Pfad zugegriffen werden:
>
> -   **./User/Vendor/MSFT/Policy/Config/ApplicationManagement/RequirePrivateStoreOnly** zum Festlegen der Richtlinie.
> -   **./User/Vendor/MSFT/Policy/Result/ApplicationManagement/RequirePrivateStoreOnly** , um das Ergebnis zu erzielen.


<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – zulassen öffentlichen und privaten Speicher.
-   1 – nur ist privaten Speicher aktiviert.

<p style="margin-left: 20px">Dies ist eine Richtlinie.

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 1.

<a href="" id="applicationmanagement-restrictappdatatosystemvolume"></a>**ApplicationManagement/RestrictAppDataToSystemVolume**  
<p style="margin-left: 20px">Gibt an, ob die Anwendungsdaten auf dem Systemlaufwerk beschränkt ist.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – nicht eingeschränkt.
-   1 – eingeschränkt.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="applicationmanagement-restrictapptosystemvolume"></a>**ApplicationManagement/RestrictAppToSystemVolume**  
<p style="margin-left: 20px">Gibt an, ob die Installation von Anwendungen auf dem Systemlaufwerk beschränkt ist.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – nicht eingeschränkt.
-   1 – eingeschränkt.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="authentication-alloweapcertsso"></a>**Authentifizierung/AllowEAPCertSSO**   
> **Hinweis**  Diese Richtlinie ist nur für Desktop in Windows 10 erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">Ermöglicht eine EAP Cert-basierte Authentifizierung für einmaliges Anmelden (SSO) Zugriff auf interne Ressourcen.

> **Wichtige**  
> Dieser Knoten muss über den folgenden Pfad zugegriffen werden:
>
> -   **./User/Vendor/MSFT/Policy/Config/Authentication/AllowEAPCertSSO** zum Festlegen der Richtlinie.
> -   **./User/Vendor/MSFT/Policy/Result/Authentication/AllowEAPCertSSO** , um das Ergebnis zu erzielen.


<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig.

<a href="" id="authentication-allowfastreconnect"></a>**Authentifizierung/AllowFastReconnect**  
<p style="margin-left: 20px">Ermöglicht es von für EAP-Methode TLS versuchte EAP schnelle Wiederherstellung der Verbindung.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="authentication-allowsecondaryauthenticationdevice"></a>**Authentifizierung/AllowSecondaryAuthenticationDevice**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Ermöglicht sekundäre Authentifizierung Geräten Windows entwickelt.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 – zulässig.

<p style="margin-left: 20px">Die Standardeinstellung für diese Richtlinie muss auf für Consumer-Geräte (definiert, als lokaler oder Microsoft-Konto Gerät verbunden) und off für Enterprise-Geräte (wie Cloud in die Domäne eingebundener, Cloud Domäne in einer Umgebung nur lokal Cloud-Domäne in einer hybridumgebung und BYOD).

<a href="" id="bitlocker-encryptionmethod"></a>**BitLocker/EncryptionMethod**  
<p style="margin-left: 20px">Gibt die BitLocker Drive Encryption-Methode und die Verschlüsselung Stärke an.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   3 - AES-128-bit
-   4 - AES 256
-   6 - XTS 128
-   7 - XTS 256

<a href="" id="bluetooth-allowadvertising"></a>**Bluetooth/AllowAdvertising**  
<p style="margin-left: 20px">Gibt an, ob Werbung Bluetooth-Geräts versenden kann.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen. Bei Festlegung auf 0 ist, das Gerät sendet nicht anzeigen. Vergewissern Sie sich, Bluetooth LE app verwenden, und aktivieren, der Werbung. Vergewissern Sie sich, dass die Ankündigung nicht durch die Peripheriegeräte empfangen wird.
-   1 (Standard) – zulässig ist. Bei Festlegung auf 1 fest, das Gerät sendet anzeigen. Vergewissern Sie sich, Bluetooth LE app verwenden, und aktivieren, der Werbung. Vergewissern Sie sich, dass die Ankündigung von der Peripheriegeräte empfangen wird.

<p style="margin-left: 20px">Wenn dies nicht festgelegt oder es gelöscht wird, wird der Standardwert von 1 (zulassen) verwendet.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="bluetooth-allowdiscoverablemode"></a>**Bluetooth/AllowDiscoverableMode**  
<p style="margin-left: 20px">Gibt an, ob andere Bluetooth-fähigen Geräte das Gerät erkennen können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen. Bei Festlegung auf 0, andere Geräte nicht erkennt das Gerät können. Öffnen Sie die Bluetooth-Steuerung auf dem Gerät, um zu überprüfen. Klicken Sie dann, wechseln Sie an ein anderes Bluetooth-aktivierten Gerät, öffnen Sie der Bluetooth-Systemsteuerung, und stellen Sie sicher, dass Sie den Namen des Geräts nicht sehen können.
-   1 (Standard) – zulässig ist. Auf 1 festgelegt, werden andere Geräte können das Gerät erkannt. Öffnen Sie die Bluetooth-Steuerung auf dem Gerät, um zu überprüfen. Klicken Sie dann, wechseln Sie an ein anderes Gerät Bluetooth-fähigen, öffnen die Bluetooth-Steuerung, und stellen Sie sicher, dass Sie es erkennen können.

<p style="margin-left: 20px">Wenn dies nicht festgelegt oder es gelöscht wird, wird der Standardwert von 1 (zulassen) verwendet.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="bluetooth-allowprepairing"></a>**Bluetooth/AllowPrepairing**  
<p style="margin-left: 20px">Gibt an, ob bestimmte gebündelten Bluetooth Peripheriegeräte automatisch mit der Host-Gerät ein.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig.

<a href="" id="bluetooth-localdevicename"></a>**Bluetooth/LocalDeviceName**  
<p style="margin-left: 20px">Der lokale Name des Bluetooth-Geräts festgelegt.

<p style="margin-left: 20px">Wenn dies festgelegt ist, wird der Wert, den diese Liste festgelegt ist, als den Namen des Bluetooth-Geräts verwendet werden. Überprüfen Sie, ob die Richtlinie festgelegt ist, öffnen Sie die Bluetooth-Steuerung auf dem Gerät befindet. Klicken Sie dann, wechseln Sie an ein anderes Bluetooth-aktivierten Gerät, öffnen Sie der Bluetooth-Systemsteuerung, und überprüfen Sie, ob der angegebene Wert.

<p style="margin-left: 20px">Wenn diese Richtlinie nicht festgelegt ist, oder es gelöscht wird, wird der Standardnamen für den lokalen Radio verwendet.

<a href="" id="bluetooth-servicesallowedlist"></a>**Bluetooth/ServicesAllowedList**  
<p style="margin-left: 20px">Legen Sie eine Liste der zulässigen Dienste und Profile. Hex formatierte Zeichenfolgenarray mit Bluetooth-Dienst-UUIDs in kanonische Form, getrennt durch Semikolons. Zum Beispiel {782AFCFC-7CAA-436C-8BF0-78CD0FFBD4AF}.

<p style="margin-left: 20px">Der Standardwert ist eine leere Zeichenfolge.

<a href="" id="browser-allowautofill"></a>**Browser/AllowAutofill**  
<p style="margin-left: 20px">Gibt an, ob auf Websites AutoAusfüllen zulässig ist.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<p style="margin-left: 20px">So überprüfen Sie AllowAutofill werden auf 0 (nicht zulässig) festgelegt:

1.  Öffnen Sie Microsoft Edge OrMicrosoft Edge für Windows 10 Mobile.
2.  Klicken Sie in der oberen rechten Ecke des Browsers **...**.
3.  Klicken Sie in der Dropdownliste auf **Einstellungen** , und wählen Sie **Erweiterte Einstellungen anzeigen**.
4.  Überprüfen Sie die Einstellung, die **, der Formulareinträge speichern** ausgegraut ist.

<a href="" id="browser-allowbrowser"></a>**Browser/AllowBrowser**  
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Mobile erzwungen und im Windows-10 für Desktop nicht unterstützt. Verwenden Sie für desktop-Geräte stattdessen die [AppLocker CSP](applocker-csp.md) .


<p style="margin-left: 20px">Gibt an, ob der Browser auf dem Gerät zulässig ist.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<p style="margin-left: 20px">Wenn diese Richtlinie auf 0 (nicht zulässig), die Microsoft-Edge für Windows 10 Mobile Kachel abgeblendet, erscheint festgelegt ist und durch Klicken auf die Kachel wird eine Meldung angezeigt, Theat beim Durchsuchen des Internets angezeigt wurde vom Systemadministrator deaktiviert.

<a href="" id="browser-allowcookies"></a>**Browser/AllowCookies**  
<p style="margin-left: 20px">Gibt an, ob Cookies zugelassen werden.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<p style="margin-left: 20px">So überprüfen Sie AllowCookies werden auf 0 (nicht zulässig) festgelegt:

1.  Öffnen Sie Microsoft Edge OrMicrosoft Edge für Windows 10 Mobile.
2.  Klicken Sie in der oberen rechten Ecke des Browsers **...**.
3.  Klicken Sie in der Dropdownliste auf **Einstellungen** , und wählen Sie **Erweiterte Einstellungen anzeigen**.
4.  Überprüfen Sie die Einstellung, die **, der Cookies** ausgegraut ist.

<a href="" id="browser-allowdevelopertools"></a>**Browser/AllowDeveloperTools**  
> **Hinweis**  Diese Richtlinie ist nur für Desktop in Windows 10 erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">Gibt an, ob Mitarbeiter F12-Entwicklertools auf Microsoft Edge verwenden können. Diese Einstellung aktivieren, oder nicht konfiguriert, kann Mitarbeiter F12-Entwicklertools verwenden. Aktivieren diese Einstellung deaktivieren Mitarbeiter aus mithilfe von Entwicklertools (F12) wird beendet.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="browser-allowdonottrack"></a>**Browser/AllowDoNotTrack**  
<p style="margin-left: 20px">Gibt an, ob nicht nachverfolgen Kopfzeilen zulässig sind.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – nicht zugelassen.
-   1 – zulässig.

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 1.

<p style="margin-left: 20px">So überprüfen Sie AllowDoNotTrack werden auf 0 (nicht zulässig) festgelegt:

1.  Öffnen Sie Microsoft Edge OrMicrosoft Edge für Windows 10 Mobile.
2.  Klicken Sie in der oberen rechten Ecke des Browsers **...**.
3.  Klicken Sie in der Dropdownliste auf **Einstellungen** , und wählen Sie **Erweiterte Einstellungen anzeigen**.
4.  Überprüfen Sie die Einstellung, die **, der Anfragen senden führen nicht nachverfolgen** ausgegraut ist.

<a href="" id="browser-allowextensions"></a>**Browser/AllowExtensions**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt an, ob Microsoft Edge Extensions zulässig sind.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zulässig.
-   1 (Standard) – zulässig ist.

<a href="" id="browser-allowinprivate"></a>**Browser/AllowInPrivate**  
<p style="margin-left: 20px">Gibt an, ob InPrivate-Browsen in Unternehmensnetzwerken zulässig ist.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="browser-allowpasswordmanager"></a>**Browser/AllowPasswordManager**  
<p style="margin-left: 20px">Gibt an, ob speichern und Verwalten von Kennwörtern lokal auf dem Gerät zulässig ist.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<p style="margin-left: 20px">So überprüfen Sie AllowPasswordManager werden auf 0 (nicht zulässig) festgelegt:

1.  Öffnen Sie Microsoft Edge OrMicrosoft Edge für Windows 10 Mobile.
2.  Klicken Sie in der oberen rechten Ecke des Browsers **...**.
3.  Klicken Sie in der Dropdownliste auf **Einstellungen** , und wählen Sie **Erweiterte Einstellungen anzeigen**.
4.  Überprüfen Sie die Einstellungen, **anbieten für Kennwort zu speichern** und **Verwalten von gespeicherten Kennwörter** abgeblendet sind.

<a href="" id="browser-allowpopups"></a>**Browser/AllowPopups**  
<p style="margin-left: 20px">Gibt an, ob Popupblocker zugelassen aktiviert oder deaktiviert ist.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – Popupblocker nicht zulässig. Dies bedeutet, dass Popupfenster Browserfenster zulässig sind.
-   1 – Popupblocker ist zugelassen oder aktiviert. Das bedeutet, dass Popupfenster Browserfenster blockiert sind.

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 1.

<p style="margin-left: 20px">So überprüfen Sie AllowPopups werden auf 0 (nicht zulässig) festgelegt:

1.  Öffnen Sie Microsoft Kante.
2.  Klicken Sie in der oberen rechten Ecke des Browsers **...**.
3.  Klicken Sie in der Dropdownliste auf **Einstellungen** , und wählen Sie **Erweiterte Einstellungen anzeigen**.
4.  Überprüfen Sie die Einstellung, die **, der Popups blocken** ausgegraut ist.

<a href="" id="browser-allowsearchsuggestionsinaddressbar"></a>**Browser/AllowSearchSuggestionsinAddressBar**  
<p style="margin-left: 20px">Gibt an, ob in der Adressleiste Suchvorschläge zulässig sind.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="browser-allowsmartscreen"></a>**Browser/AllowSmartScreen**  
<p style="margin-left: 20px">Gibt an, ob SmartScreen zulässig ist.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 1.

<p style="margin-left: 20px">So überprüfen Sie AllowSmartScreen werden auf 0 (nicht zulässig) festgelegt:

1.  Öffnen Sie Microsoft EdgeorMicrosoft Edge für 10 Windows Mobile.
2.  Klicken Sie in der oberen rechten Ecke des Browsers **...**.
3.  Klicken Sie in der Dropdownliste auf **Einstellungen** , und wählen Sie **Erweiterte Einstellungen anzeigen**.
4.  Überprüfen Sie die Einstellung, die **, der Hilfe Schutz vor böswilligen Websites, und Laden Sie mit SmartScreen-Filter** ausgegraut ist.

<a href="" id="browser-enterprisemodesitelist"></a>**Browser/EnterpriseModeSiteList**  
> **Hinweis**  Diese Richtlinie ist nur für Desktop in Windows 10 erzwungen und in Windows 10 Mobile nicht unterstützt.

 
<p style="margin-left: 20px">Ermöglicht dem Benutzer eine Liste eine Enterprise-Website-URL angeben.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   Nicht konfiguriert. Das Gerät sucht nach Updates von Microsoft Update.
-   Legen Sie auf die Liste der Enterprise-Website einen URL-Speicherort.

<a href="" id="browser-firstrunurl"></a>**Browser/FirstRunURL**  
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Mobile erzwungen und im Windows-10 für Desktop nicht unterstützt.


<p style="margin-left: 20px">Gibt die URL für Windows 10 Mobile Microsoft Kante. verwenden, wenn es das erste Mal geöffnet wird.

<p style="margin-left: 20px">Der Datentyp ist eine Zeichenfolge.

<p style="margin-left: 20px">Der Standardwert ist eine leere Zeichenfolge. Andernfalls sollte die Zeichenfolge enthalten die URL der Webseite sehen Benutzer beim ersten Microsoft Edge ausgeführt wird. Zum Beispiel "contoso.com".

<a href="" id="browser-homepages"></a>**Browser/Homepages**   
> **Hinweis**  Diese Richtlinie ist nur verfügbar für Windows 10 für Desktop und in Windows 10 Mobile nicht unterstützt.

 
<p style="margin-left: 20px">Gibt die Start-Seiten für Geräte MDM registriert. Benutzer können diese Einstellung ändern. Aktivieren dieser Einstellung können Sie eine oder mehrere corporate Startseiten konfigurieren. Wenn diese Einstellung aktiviert ist, muss auch enthalten URLs auf die Seiten, trennen mehrere Seiten mithilfe von XML-Escapezeichen Zeichen **&lt;** und **&gt;**. Beispielsweise "&lt;support.contoso.com&gt;&lt;support.microsoft.com&gt;"

<p style="margin-left: 20px">Starten im Windows-10, Version 1607 verwenden, wird diese Richtlinie erzwungen werden, damit die durch diese Richtlinie angegebenen Start-Seiten von den Benutzern nicht geändert werden können.

> **Hinweis**  Wenn Sie diese Einstellung deaktivieren oder nicht konfigurieren, wird das standardmäßige Startseiten auf Webseiten in App-Einstellungen angegeben.


<a href="" id="browser-preventaccesstoaboutflagsinmicrosoftedge"></a>**Browser/PreventAccessToAboutFlagsInMicrosoftEdge**  
<p style="margin-left: 20px">Gibt an, ob Benutzer zugreifen können, die über: Flags-Seite, der Entwickler Einstellungen ändern und zum Aktivieren von experimentelle Features verwendet wird.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – Benutzer können zugreifen, die über: Flags-Seite in Microsoft Edge.
-   1 – Benutzer keinen Zugriff auf die zu: Flags-Seite in Microsoft Edge.

<a href="" id="browser-preventsmartscreenpromptoverride"></a>**Browser/PreventSmartScreenPromptOverride**  
<p style="margin-left: 20px">Gibt an, ob Benutzer die SmartScreen-Filter Warnungen zu potenziell gefährliche Websites außer Kraft setzen können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – deaktiviert.
-   1 – auf.

<p style="margin-left: 20px">Aktivieren diese Einstellung verhindert, dass Benutzer aus die SmartScreen-Filter-Warnungen ignorieren und auf der Website verhindert. Diese Einstellung deaktivieren oder nicht konfigurieren, können Benutzer zu potenziell gefährliche Websites und zum weiter zur Website die SmartScreen-Filter-Warnungen ignoriert.

<a href="" id="browser-preventsmartscreenpromptoverrideforfiles"></a>**Browser/PreventSmartScreenPromptOverrideForFiles**  
<p style="margin-left: 20px">Gibt an, ob Benutzer die Warnungen SmartScreen-Filter zum Herunterladen von nicht überprüfte Dateien außer Kraft setzen können. Aktivieren diese Einstellung verhindert, dass Benutzer aus die SmartScreen-Filter-Warnungen ignorieren und verhindert, nicht überprüfte Dateien herunterladen. Ist diese Einstellung deaktiviert oder nicht konfiguriert, kann Benutzer die SmartScreen-Filter Warnungen zu nicht überprüfte Dateien ignoriert und sie dem Download fortzufahren.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – deaktiviert.
-   1 – auf.

<a href="" id="browser-preventusinglocalhostipaddressforwebrtc"></a>**Browser/PreventUsingLocalHostIPAddressForWebRTC**  
> **Hinweis**  Diese Richtlinie ist nur für Desktop in Windows 10 erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">Gibt an, ob beim Tätigen von Anrufen über das Protokoll WebRTC Localhost IP-Adresse eines Benutzers angezeigt wird. Aktivieren diese Einstellung blendet Localhost IP-Adresse des Benutzers beim Tätigen von Telefonanrufen mit WebRTC aus. Aktivieren diese Einstellung deaktiviert oder nicht konfiguriert, zeigt ein <p style="margin-left: 20px">des Benutzers "localhost" IP-Adresse beim Tätigen von Telefonanrufen mit WebRTC.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – wird die IP-Adresse "localhost" angezeigt.
-   1 – die Localhost-IP-Adresse ist ausgeblendet.

<a href="" id="browser-sendintranettraffictointernetexplorer"></a>**Browser/SendIntranetTraffictoInternetExplorer**  
> **Hinweis**  Diese Richtlinie ist nur für Desktop in Windows 10 erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">Gibt an, ob Datenverkehr im Intranet, Internet Explorer über senden.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – wird Datenverkehr im Intranet, Internet Explorer gesendet.
-   1 – Intranet Datenverkehr wird an Microsoft Edge gesendet.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="browser-showmessagewhenopeningsitesininternetexplorer"></a>**Browser/ShowMessageWhenOpeningSitesInInternetExplorer**   
> **Hinweis**  Diese Richtlinie ist nur für Desktop in Windows 10 erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt an, ob Benutzer angezeigt werden sollte eine vollständige interstitielles Seite in Microsoft Edge beim Öffnen von Websites, die konfiguriert werden, um in Internet Explorer mithilfe der Liste der Enterprise-Website zu öffnen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – werden interstitielles Seiten nicht angezeigt.
-   1 – interstitielles Seiten werden angezeigt.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="camera-allowcamera"></a>**Kamera/AllowCamera**  
<p style="margin-left: 20px">Aktiviert oder deaktiviert die Kamera.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="connectivity-allowbluetooth"></a>**Konnektivität/AllowBluetooth**  
<p style="margin-left: 20px">Kann der Benutzer zum Aktivieren von Bluetooth oder Einschränken des Zugriffs.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht Bluetooth zulassen. Wenn diese Eigenschaft auf 0 gesetzt ist, der Sender in der Systemsteuerung Bluetooth abgeblendet und der Benutzer werden nicht Bluetooth aktivieren.
-   1 – reserviert. Wenn diese Eigenschaft auf 1 gesetzt ist, der Sender in der Bluetooth-Systemsteuerung wird funktionsfähig ist und dem Benutzer möglich Bluetooth aktivieren.

    > **Hinweis**  Dieser Wert wird in Windows Phone 8.1 MDM und EAS, Windows-10 für Desktop oder Windows 10 Mobile nicht unterstützt.

-   2 (Standard) – Bluetooth zulassen. Wenn dies auf 2 festgelegt ist, der Sender in der Bluetooth-Systemsteuerung wird funktionsfähig ist und der Benutzer wird in der Lage, Bluetooth aktivieren.

<p style="margin-left: 20px">Wenn dies nicht festgelegt ist oder es gelöscht wird, wird der Standardwert von 2 (zulassen).

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="connectivity-allowcellulardata"></a>**Konnektivität/AllowCellularData**  
<p style="margin-left: 20px">Ermöglicht den Kanal Mobilfunk-Daten auf dem Gerät. Gerät einen Neustart ist nicht erforderlich, um die Richtlinie zu erzwingen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – lässt nicht den Kanal Mobilfunk-Daten. Der Benutzer kann aktiviert werden. Dieser Wert wird in Windows 10, Version 1511 nicht unterstützt.
-   1 (Standard) – zulassen den Kanal Mobilfunk-Daten. Der Benutzer kann diese Funktion deaktivieren.
-   2 - ermöglichen Sie den Kanal Mobilfunk-Daten. Der Benutzer kann nicht deaktivieren.

<a href="" id="connectivity-allowcellulardataroaming"></a>**Konnektivität/AllowCellularDataRoaming**  
<p style="margin-left: 20px">Zugelassen oder verweigert Mobilfunk-Daten auf dem Gerät roaming. Gerät einen Neustart ist nicht erforderlich, um die Richtlinie zu erzwingen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – lässt das roaming Mobilfunk-Daten nicht. Der Benutzer kann aktiviert werden. Dieser Wert wird in Windows 10, Version 1511 nicht unterstützt.
-   1 (Standard) – zulassen Mobilfunk-Daten-roaming.
-   2 - zulassen Sie Mobilfunk-Daten auf roaming. Der Benutzer kann nicht deaktivieren.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<p style="margin-left: 20px">Um zu überprüfen, kann Unternehmen bestätigen, indem das roaming der UX-Switch aktivieren beobachten Es wird inaktiv sein, wenn die Richtlinie roaming von der Unternehmensrichtlinie erzwungen wird.

<p style="margin-left: 20px">Gehen Sie wie folgt vor, um auf mobilen Geräten zu überprüfen:

1.  Wechseln Sie zur Mobilfunk & SIM.
2.  Klicken Sie auf der SIM (neben dem Symbol für die Signalstärke), und wählen Sie **Eigenschaften**aus.
3.  Wählen Sie auf der Eigenschaftenseite **Optionen für servergespeicherte**aus.

<a href="" id="connectivity-allownfc"></a>**Konnektivität/AllowNFC**  
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Mobile erzwungen und im Windows-10 für Desktop nicht unterstützt.


<p style="margin-left: 20px">Zugelassen oder in der Nähe Feld Kommunikation (NFK) auf dem Gerät verweigert.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – lässt nicht NFK Funktionen.
-   1 (Standard) – Funktionen NFK zulassen.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="connectivity-allowusbconnection"></a>**Konnektivität/AllowUSBConnection**   
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Mobile erzwungen und im Windows-10 für Desktop nicht unterstützt.


<p style="margin-left: 20px">Ermöglicht die USB-Verbindung zwischen dem Gerät und einen Computer zum Synchronisieren von Dateien mit dem Gerät oder Entwicklertools zum Bereitstellen und Debuggen Applikationen verwenden. Ändern diese Richtlinie wirkt USB aufgeladen sich nicht.

<p style="margin-left: 20px">Media Transfer Protocol (MTP) und IP über USB werden deaktiviert, wenn diese Richtlinie erzwungen wird.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="connectivity-allowvpnovercellular"></a>**Konnektivität/AllowVPNOverCellular**  
<p style="margin-left: 20px">Gibt an, welche Art von zugrunde liegenden Verbindungen mit VPN zulässig ist.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – VPN ist nicht über Mobiltelefone zulässig.
-   1 (Standard) – können VPN eine Verbindung, einschließlich Mobilfunk.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="connectivity-allowvpnroamingovercellular"></a>**Konnektivität/AllowVPNRoamingOverCellular**  
<p style="margin-left: 20px">Verhindert, dass das Gerät mit VPN verbinden, wenn das Gerät über Mobilfunknetze wechselt.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="cryptography-allowfipsalgorithmpolicy"></a>**Kryptografie/AllowFipsAlgorithmPolicy**  
<p style="margin-left: 20px">Zugelassen oder verweigert die Richtlinie Federal Information Processing Standard (FIPS).

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – nicht zugelassen.
-   1 – zugelassen.

<a href="" id="cryptography-tlsciphersuites"></a>**Kryptografie/TLSCipherSuites**  
<p style="margin-left: 20px">Listet die Verschlüsselungsanbieter-Verschlüsselungsalgorithmen für SSL-Verbindungen zulässig. Format ist eine durch Semikolons getrennte Liste. Schreiben Sie zuletzt Win.

<a href="" id="dataprotection-allowdirectmemoryaccess"></a>**DataProtection/AllowDirectMemoryAccess**  
<p style="margin-left: 20px">Direkter Speicherzugriff ermöglicht.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="dataprotection-legacyselectivewipeid"></a>**DataProtection/LegacySelectiveWipeID**   
> **Wichtige**  Diese Richtlinie kann in einer zukünftigen Version zu ändern. Es kann zu Testzwecken verwendet werden, aber es sollte zu diesem Zeitpunkt nicht in einer produktionsumgebung verwendet werden.

 
<p style="margin-left: 20px">Festlegen, der von Windows 8.1 selektive Wischen verwendet.

> **Hinweis**  Diese Richtlinie wird nicht für die Verwendung in Windows 10 empfohlen.


<a href="" id="defender-allowarchivescanning"></a>**Defender/AllowArchiveScanning**  
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.


<p style="margin-left: 20px">Zugelassen oder verweigert Archive scannen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – zulässig ist.
-   1 (Standard) – nicht zulässig.

<a href="" id="defender-allowbehaviormonitoring"></a>**Defender/AllowBehaviorMonitoring**  
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.

 
<p style="margin-left: 20px">Zugelassen oder verweigert Windows Defender Verhalten Monitoring Funktionalität.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – zulässig ist.
-   1 (Standard) – nicht zulässig.

<a href="" id="defender-allowcloudprotection"></a>**Defender/AllowCloudProtection**  
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.


<p style="margin-left: 20px">Um Ihren PC zu schützen, wird Windows Defender Informationen an Microsoft zu Problemen senden gefundenen. Microsoft wird diese Informationen analysieren, erfahren Sie mehr über bei Ihnen und anderen Kunden und verbesserte Lösungen anzubieten.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="defender-allowemailscanning"></a>**Defender/AllowEmailScanning**  
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.


<p style="margin-left: 20px">Zugelassen oder verweigert Scannen von e-Mails.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – nicht zugelassen.
-   1 – zulässig.

<a href="" id="defender-allowfullscanonmappednetworkdrives"></a>**Defender/AllowFullScanOnMappedNetworkDrives**  
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.


<p style="margin-left: 20px">Zugelassen oder einen vollständigen Scan der zugeordneten Netzlaufwerke verweigert.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – nicht zugelassen.
-   1 – zulässig.

<a href="" id="defender-allowfullscanremovabledrivescanning"></a>**Defender/AllowFullScanRemovableDriveScanning**  
> **Hinweis**  Mit dieser Richtlinie wird nur für Desktop in Windows 10 erzwungen.


<p style="margin-left: 20px">Zugelassen oder einen vollständigen Scan der Wechseldatenträger verweigert.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="defender-allowintrusionpreventionsystem"></a>**Defender/AllowIntrusionPreventionSystem**  
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.


<p style="margin-left: 20px">Zugelassen oder verweigert Windows Defender Intrusionsprävention Funktionalität.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="defender-allowioavprotection"></a>**Defender/AllowIOAVProtection**  
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.

 
<p style="margin-left: 20px">Zugelassen oder verweigert Windows Defender IOAVP Protection-Funktionalität.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="defender-allowonaccessprotection"></a>**Defender/AllowOnAccessProtection**  
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.


<p style="margin-left: 20px">Zugelassen oder verweigert Windows Defender für den Zugriffsschutz-Funktionalität.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="defender-allowrealtimemonitoring"></a>**Defender/AllowRealtimeMonitoring**  
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.


<p style="margin-left: 20px">Zugelassen oder verweigert Windows Defender Monitoring in Echtzeit-Funktionalität.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="defender-allowscanningnetworkfiles"></a>**Defender/AllowScanningNetworkFiles**  
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.

 
<p style="margin-left: 20px">Zugelassen oder eine Überprüfung der Netzwerkdateien verweigert.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="defender-allowscriptscanning"></a>**Defender/AllowScriptScanning**  
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.


<p style="margin-left: 20px">Zugelassen oder verweigert Windows Defender Script-Scans Funktionalität.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="defender-allowuseruiaccess"></a>**Defender/AllowUserUIAccess**  
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.


<p style="margin-left: 20px">Ermöglicht oder verweigert den Benutzerzugriff auf die Windows Defender-Benutzeroberfläche. Wenn nicht zulässig ist, werden auch alle Windows Defender Benachrichtigungen unterdrückt.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="defender-avgcpuloadfactor"></a>**Defender/AVGCPULoadFactor**  
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.

 
<p style="margin-left: 20px">Stellt den durchschnittlichen CPU-Auslastungsfaktor für die Überprüfung Windows Defender (in Prozent).

<p style="margin-left: 20px">Gültige Werte: 0 bis 100

<p style="margin-left: 20px">Der Standardwert ist 50.

<a href="" id="defender-daystoretaincleanedmalware"></a>**Defender/DaysToRetainCleanedMalware**   
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.

 
<p style="margin-left: 20px">Zeitraum (in Tagen), die isoliert werden Elemente im System gespeichert.

<p style="margin-left: 20px">Gültige Werte: 0 bis 90

<p style="margin-left: 20px">Der Standardwert ist 0 (null) vermeidet eine Verbindung zwischen Elementen in Quarantäne und nicht automatisch entfernt.

<a href="" id="defender-excludedextensions"></a>**Defender/ExcludedExtensions**   
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.

 
<p style="margin-left: 20px">ermöglicht Ihnen ein Administrator eine Liste der Datei angeben Geben Extensions während eines Überprüfungsvorgangs ignoriert werden sollen. Jeden Dateityp in der Liste muss getrennt werden, indem eine **|**. Beispielsweise "Lib | Obj".

<a href="" id="defender-excludedpaths"></a>**Defender/ExcludedPaths**   
> **Hinweis**  Mit dieser Richtlinie wird nur für Desktop in Windows 10 erzwungen.


<p style="margin-left: 20px">Ermöglicht einem Administrator das angeben eine Liste Directory Pfade, die während eines Überprüfungsvorgangs ignoriert wird. Jeder Pfad in der Liste getrennt werden muss, durch eine **|**. Beispielsweise "C:\\Beispiel | C:\\Beispiel 1 ".

<a href="" id="defender-excludedprocesses"></a>**Defender/ExcludedProcesses**   
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.


<p style="margin-left: 20px">Ermöglicht einem Administrator das angeben eine Liste von Dateien, die von Prozessen, um während eines Überprüfungsvorgangs ignorieren geöffnet.

> **Wichtig**  Der Prozess selbst wird nicht von der Überprüfung ausgeschlossen, jedoch kann mithilfe der Richtlinie **Defender/ExcludedPaths** des Pfads ausgeschlossen werden.

 
<p style="margin-left: 20px">Jeden Dateityp muss getrennt werden, indem eine **|**. Beispielsweise "C:\\Example.exe| C:\\Example1.exe ".

<a href="" id="defender-puaprotection"></a>**Defender/PUAProtection**   
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.


<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt den Grad der Erkennung für unerwünschte Applications (PUAs). Windows Defender gewarnt, wenn unerwünschter Software heruntergeladen werden oder versucht, sich auf Ihrem Computer installieren.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – PUA Schutz deaktiviert. Windows Defender bietet keinen Schutz vor unerwünschten Applications.
-   1 – PUA Schutz auf. Erkannte Elemente werden blockiert. Sie werden im Verlauf zusammen mit anderen Bedrohungen angezeigt.
-   2 – Überwachungsmodus aktiviert. Windows Defender unerwünschte Applikationen erkennen, aber keine Aktion ausgeführt. Sie können Informationen zu den Anwendungen, dass Windows Defender gegen benutzt haben würde durch Suchen des Ereignisse, die in den Ereignisdetails Viewer von Windows Defender erstellt ansehen.

<a href="" id="defender-realtimescandirection"></a>**Defender/RealTimeScanDirection**  
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.


<p style="margin-left: 20px">Steuert, welche Dateigruppen überwacht werden sollen.

> **Hinweis**  Wenn **AllowOnAccessProtection** nicht zulässig ist, kann diese Konfiguration verwendet werden, um bestimmte Dateien zu überwachen.


<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – überwachen Sie alle Dateien (bidirektionale).
-   1 – Überwachen Sie eingehende Dateien.
-   2 – überwachen Sie ausgehende Dateien.

<a href="" id="defender-scanparameter"></a>**Defender/ScanParameter**  
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.


<p style="margin-left: 20px">Legt fest, ob eine schnelle Scan- oder der vollständigen Scan ausführen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   1 (Standard) – schnell-scan
-   2 – vollständige Überprüfung

<a href="" id="defender-schedulequickscantime"></a>**Defender/ScheduleQuickScanTime**  
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.

 
<p style="margin-left: 20px">Wählt die Tageszeit, die der Windows Defender schnelle-Scan ausgeführt werden soll.

> **Hinweis**  Die Überprüfung wird richtet sich nach welchen Überprüfung in der Einstellung **Defender/ScanParameter** ausgewählt ist.

 
<p style="margin-left: 20px">Gültige Werte: 0 – 1380

<p style="margin-left: 20px">Angenommen, der Wert 0 = 12:00 Uhr, einen Wert von 60 = 1:00 Uhr, einen Wert von 120 = 2:00 und so weiter bis zu einem Wert von 1380 = 11:00 Uhr.

<p style="margin-left: 20px">Der Standardwert ist 120 <a href="" id="defender-schedulescanday"></a> **Defender/ScheduleScanDay**  
> **Hinweis** diese Richtlinie wird nur für Desktop in Windows 10 erzwungen.


<p style="margin-left: 20px">Wählt den Tag, den die Überprüfung Windows Defender ausgeführt werden soll.

> **Hinweis**  Die Überprüfung wird richtet sich nach welchen Überprüfung in der Einstellung **Defender/ScanParameter** ausgewählt ist.


<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – täglich
-   1 – Montag
-   2 – Dienstag
-   3 – Mittwoch
-   4 – Donnerstag
-   5 – Freitag
-   6 – Samstag
-   7 – Sonntag
-   8 – es wird kein geplanter scan

<a href="" id="defender-schedulescantime"></a>**Defender/ScheduleScanTime**  
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.


<p style="margin-left: 20px">Wählt die Tageszeit die Überprüfung Windows Defender ausgeführt werden soll.

> **Hinweis**  Die Überprüfung wird richtet sich nach welchen Überprüfung in der Einstellung **Defender/ScanParameter** ausgewählt ist.


<p style="margin-left: 20px">Gültige Werte: 0 – 1380.

<p style="margin-left: 20px">Angenommen, der Wert 0 = 12:00 Uhr, einen Wert von 60 = 1:00 Uhr, einen Wert von 120 = 2:00 und so weiter bis zu einem Wert von 1380 = 11:00 Uhr.

<p style="margin-left: 20px">Der Standardwert ist 120.

<a href="" id="defender-signatureupdateinterval"></a>**Defender/SignatureUpdateInterval**   
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.

 
<p style="margin-left: 20px">Gibt das Intervall (in Stunden), das verwendet werden überprüft für Signaturen, sodass statt der ScheduleDay und ScheduleTime die Überprüfung auf neue Signaturen gemäß den das Intervall festgelegt wird.

<p style="margin-left: 20px">Gültige Werte: 0 bis 24.

<p style="margin-left: 20px">Der Wert 0 bedeutet, dass keine Überprüfung nach neuen Signaturen, einen Wert von 1 bedeutet, dass stündlich, einen Wert von 2 bedeutet, dass alle zwei Stunden, und so weiter bis zu einem Wert von 24, überprüfen Sie d. h., die täglich überprüfen überprüfen.

<p style="margin-left: 20px">Der Standardwert ist 8.

<a href="" id="defender-submitsamplesconsent"></a>**Defender/SubmitSamplesConsent**   
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.

 
<p style="margin-left: 20px">Überprüft, ob der Benutzer stimmen Ebene in Windows Defender zum Senden von Daten. Wenn bereits die erforderliche Zustimmung erteilt wurde, sendet Windows Defender. Wenn dies nicht der Fall ist, (und wenn der Benutzer nie zu bitten angegeben wurde), die Benutzeroberfläche wird gestartet, um Kundensupport Zustimmung des Benutzers (Wenn **Defender/AllowCloudProtection** zulässig ist) vor dem Senden von Daten.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – immer anfordern.
-   1 (Standard) – senden Beispiele für sichere automatisch.
-   2 – nie senden.
-   3 – automatisch alle Beispiele zu senden.

<a href="" id="defender-threatseveritydefaultaction"></a>**Defender/ThreatSeverityDefaultAction**  
> **Hinweis**  Diese Richtlinie ist nur in Windows-10 für Desktop erzwungen.
 

<p style="margin-left: 20px">Ermöglicht einem Administrator können Sie eine beliebige gültige Bedrohung Schweregrade und die entsprechenden Standard-Aktions-ID auszuführende angeben.

<p style="margin-left: 20px">Dieser Wert ist eine Liste der Schweregrad Bedrohung IDs und die entsprechenden Aktionen, getrennt durch ein**|** im Format "*veränderte*=*Aktion*|*veränderte*=*Aktion*". Zum Beispiel "1 = 6 | 2 = 2 | 4 = 10 | 5 = 3

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte für Schweregrade Bedrohung:

-   1 – niedriger Schweregrad Bedrohungen
-   2 – mittlerer Schweregrad Bedrohungen
-   4 – hoher Schweregrad Bedrohungen
-   5 – erheblich Bedrohungen

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte für mögliche Aktionen:

-   1 – bereinigen
-   2 – Quarantäne
-   3 – Entfernen
-   6 – zulassen
-   8 – benutzerdefinierte
-   10 – blockieren

<a href="" id="deliveryoptimization-doabsolutemaxcachesize"></a>**DeliveryOptimization/DOAbsoluteMaxCacheSize**  
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Pro Enterprise und Bildungseinrichtungen Editionen erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt die maximale Größe in GB der Übermittlung Optimierung Cache. Diese Richtlinie setzt die DOMaxCacheSize Richtlinie außer Kraft. Der Wert 0 (null) bedeutet "Unbegrenzt" Cache. Übermittlung Optimierung wird den Cache gelöscht, wenn das Gerät über wenig Speicherplatz verfügt.

<p style="margin-left: 20px">Der Standardwert ist 10.

<a href="" id="deliveryoptimization-dodownloadmode"></a>**DeliveryOptimization/DODownloadMode**   
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Pro Enterprise und Bildungseinrichtungen Editionen erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">Gibt die Downloadmethode, die App aktualisiert und Übermittlung Optimierung in Downloads von Windows-Updates, Apps verwenden können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nur HTTP, keine peering.
-   1 (Standard) – HTTP gemischt mit peering hinter den gleichen NAT-Gerät
-   2 – HTTP gemischt mit peering über eine private Gruppe. Peering erfolgt in der Standardeinstellung auf Geräten in der gleichen Active Directory-Standort (falls vorhanden) oder der gleichen Domäne. Wenn diese Option ausgewählt ist, wird die peering NATs schneidet. Zum Erstellen eine benutzerdefinierte Gruppe Gruppen-ID in Kombination mit 2-Modus verwenden.
-   3 – HTTP gemischt mit peering Internet.
-   99 - einfacher Downloadmodus mit keine peering. Übermittlung Optimierung lädt nur über HTTP und kein Versuch, wenden Sie sich an die Zustellung Optimierung Cloud Services. In Windows 10, Version 1607 hinzugefügt.
-   100 - Bypass-Modus. Verwenden Sie Übermittlung Optimierung und verwenden Sie stattdessen BITS nicht. In Windows 10, Version 1607 hinzugefügt.

<a href="" id="deliveryoptimization-dogroupid"></a>**DeliveryOptimization/DOGroupID**  
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Pro Enterprise und Bildungseinrichtungen Editionen erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">Diese Richtlinie gibt eine beliebige Gruppen-ID, zu dem das Gerät gehört. Verwenden Sie diese Option, wenn Sie eine einzige Gruppe für lokales Netzwerk Peering in den Zweigstellen zu erstellen, die in verschiedenen Domänen oder sind nicht in demselben LAN müssen. Beachten Sie, dass dies eine best Effort Optimierung ist und sollte nicht auf für die Authentifizierung der Identität verlassen.

> **Hinweis**  Verwenden Sie eine GUID als die Kennung.


<a href="" id="deliveryoptimization-domaxcacheage"></a>**DeliveryOptimization/DOMaxCacheAge**  
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Pro Enterprise und Bildungseinrichtungen Editionen erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">Gibt die maximale Zeit in Sekunden an, denen jede Datei im Cache Übermittlung Optimierung aufbewahrt wird, nachdem erfolgreich herunterladen. Der Wert 0 (null) bedeutet "Unbegrenzt" Übermittlung Optimierung die Dateien im Cache länger enthält, und die Dateien zur Verfügung stellen für inhaltsuploads auf anderen Geräten, solange die Cachegröße nicht überschritten hat. Der Wert 0 ist neu in Windows 10, Version 1607.

<p style="margin-left: 20px">Der Standardwert ist 259200 Sekunden (3 Tage).

<a href="" id="deliveryoptimization-domaxcachesize"></a>**DeliveryOptimization/DOMaxCacheSize**   
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Pro Enterprise und Bildungseinrichtungen Editionen erzwungen und in Windows 10 Mobile nicht unterstützt.

 
<p style="margin-left: 20px">Gibt die maximale Cachegröße, die Optimierung der Bereitstellung verwendet werden kann, als Prozentsatz der Datenträgergröße (1-100).

<p style="margin-left: 20px">Der Standardwert ist 20.

<a href="" id="deliveryoptimization-domaxdownloadbandwidth"></a>**DeliveryOptimization/DOMaxDownloadBandwidth**   
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Pro Enterprise und Bildungseinrichtungen Editionen erzwungen und in Windows 10 Mobile nicht unterstützt.
 

<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt die maximale Download-Bandbreite in KB/Sekunde an, die das Gerät bei allen Übermittlung Optimierung von gleichzeitigen Download-Aktivitäten verwenden kann.

<p style="margin-left: 20px">Der Standardwert 0 (null) bedeutet, dass Übermittlung Optimierung dynamisch angepasst wird, um die verfügbare Bandbreite für Downloads zu verwenden.

<a href="" id="deliveryoptimization-domaxuploadbandwidth"></a>**DeliveryOptimization/DOMaxUploadBandwidth**   
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Pro Enterprise und Bildungseinrichtungen Editionen erzwungen und in Windows 10 Mobile nicht unterstützt.

 
<p style="margin-left: 20px">Gibt die maximale Uploadgröße Bandbreite in KB/Sekunde an, die über alle Aktivitäten zu gleichzeitige hochladen Übermittlung Optimierung von einem Gerät verwendet werden soll.

<p style="margin-left: 20px">Der Standardwert ist 0 (null) und unbegrenzte mögliche Bandbreite (optimiert für minimaler Auslastung der Bandbreite zum Hochladen) ermöglicht.

<a href="" id="deliveryoptimization-dominbackgroundqos"></a>**DeliveryOptimization/DOMinBackgroundQos**   
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Pro Enterprise und Bildungseinrichtungen Editionen erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt den minimalen Download QoS (Quality of Service oder Geschwindigkeit) in Kbit/s für Hintergrund Downloads. Diese Richtlinie wirkt sich auf das Mischen von Peer und HTTP Quellen. Übermittlung Optimierung ergänzt den Download aus der Quelle HTTP, um den Mindestsatz der QoS-Wert zu erzielen.

<p style="margin-left: 20px">Der Standardwert beträgt 500.

<a href="" id="deliveryoptimization-domodifycachedrive"></a>**DeliveryOptimization/DOModifyCacheDrive**   
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Pro Enterprise und Bildungseinrichtungen Editionen erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt das Laufwerk, das Zustellung Optimierung für den Cache verwendet werden soll. Laufwerk kann mithilfe von Umgebungsvariablen, Laufwerkbuchstabe oder mithilfe eines vollständigen Pfads angegeben werden.

<p style="margin-left: 20px">Standardmäßig wird Systemlaufwerk % verwendet, um den Cache zu speichern.

<a href="" id="deliveryoptimization-domonthlyuploaddatacap"></a>**DeliveryOptimization/DOMonthlyUploadDataCap**   
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Pro Enterprise und Bildungseinrichtungen Editionen erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt die maximale Gesamtanzahl Bytes in GB, die Zustellung Optimierung Internet Peers pro Kalendermonat hochladen darf an.

<p style="margin-left: 20px">Der Wert 0 (null) bedeutet "Unbegrenzt" Unbegrenzt Upload monatliche wird angewendet, wenn 0 festgelegt ist.

<p style="margin-left: 20px">Der Standardwert ist 20.

<a href="" id="deliveryoptimization-dopercentagemaxdownloadbandwidth"></a>**DeliveryOptimization/DOPercentageMaxDownloadBandwidth**   
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Pro Enterprise und Bildungseinrichtungen Editionen erzwungen und in Windows 10 Mobile nicht unterstützt.

 
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt die maximale Download Bandbreite, die Zustellung Optimierung bei allen gleichzeitigen Download Aktivitäten als Prozentsatz des verfügbaren Download Bandbreite verwendet.

<p style="margin-left: 20px">Der Standardwert 0 (null) bedeutet, dass Übermittlung Optimierung dynamisch angepasst wird, um die verfügbare Bandbreite für Downloads zu verwenden.

<a href="" id="devicelock-allowidlereturnwithoutpassword"></a>**DeviceLock/AllowIdleReturnWithoutPassword**   
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Mobile erzwungen und im Windows-10 für Desktop nicht unterstützt.

 
<p style="margin-left: 20px">Gibt an, ob Benutzereingaben müssen eine PIN oder das Kennwort, wenn das Gerät aus Leerlauf fortgesetzt.

> **Hinweis**  Diese Richtlinie muss in einem unteilbare Befehl eingeschlossen werden.

 
<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="devicelock-allowscreentimeoutwhilelockeduserconfig"></a>**DeviceLock/AllowScreenTimeoutWhileLockedUserConfig**  
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Mobile erzwungen und im Windows-10 für Desktop nicht unterstützt.

 
<p style="margin-left: 20px">Gibt an, ob eine konfigurierbare Einstellung das Timeout Bildschirm klicken Sie auf dem Sperrbildschirm Windows 10 Mobile Geräte zu steuern.

> **Hinweis**  Diese Richtlinie muss in einem unteilbare Befehl eingeschlossen werden.


<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – nicht zugelassen.
-   1 – zulässig.

> **Wichtig**  Wenn diese Richtlinie auf 1 (zugelassen) festgelegt ist, wird der Wert festlegen, indem **DeviceLock/ScreenTimeOutWhileLocked** ignoriert. Damit Enterprise Kontrolle über den Bildschirm Timeout sichergestellt ist, legen Sie diese Richtlinie auf 0 (nicht zulässig), und verwenden Sie **DeviceLock/ScreenTimeOutWhileLocked** die Timeoutdauer Bildschirm festgelegt.


<a href="" id="devicelock-allowsimpledevicepassword"></a>**DeviceLock/AllowSimpleDevicePassword**  
<p style="margin-left: 20px">Gibt an, ob PINs oder Kennwörter wie "1111" oder "1234" zulässig sind. Für den Desktop steuert es auch die Verwendung der Bild-Kennwörter.

> **Hinweis**  Diese Richtlinie muss in einem unteilbare Befehl eingeschlossen werden.


<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Weitere Informationen zu dieser Richtlinie finden Sie unter [Exchange ActiveSync-Richtlinie Engine Overview](https://technet.microsoft.com/library/dn282287.aspx).

<a href="" id="devicelock-alphanumericdevicepasswordrequired"></a>**DeviceLock/AlphanumericDevicePasswordRequired**  
<p style="margin-left: 20px">Bestimmt den Typ des PIN oder erforderliche Kennwort. Diese Richtlinie gilt nur, wenn die **DeviceLock/DevicePasswordEnabled** -Richtlinie auf 0 (erforderlich) festgelegt ist.

> **Hinweis**  
> Diese Richtlinie muss in einem unteilbare Befehl eingeschlossen werden.
>
> Verwenden Sie den Befehl Replace immer anstelle von hinzufügen für diese Richtlinie in Windows 10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen).


<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – alphanumerische PIN oder erforderliche Kennwort.
-   1 – numerische PIN oder erforderliche Kennwort.
-   2 (Standard) – Benutzer können auswählen: numerische PIN oder Kennwort verwenden aus, oder alphanumerische PIN oder Kennwort.

> **Hinweis**  
> Wenn **AlphanumericDevicePasswordRequired** auf 1 oder 2, klicken Sie dann MinDevicePasswordLength festgelegt ist = 0 und MinDevicePasswordComplexCharacters = 1.
>
> Wenn **AlphanumericDevicePasswordRequired** auf 0, klicken Sie dann MinDevicePasswordLength festgelegt ist = 4 und MinDevicePasswordComplexCharacters = 2.

 
<a href="" id="devicelock-devicepasswordenabled"></a>**DeviceLock/DevicePasswordEnabled**  
<p style="margin-left: 20px">Gibt an, ob Gerätesperre aktiviert ist.

> **Hinweis**  
> Diese Richtlinie muss in einem unteilbare Befehl eingeschlossen werden.
>
> Verwenden Sie immer den Befehl Replace anstelle von hinzufügen für diese Richtlinie in Windows 10 für desktop-Editionen.
 

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – aktiviert
-   1 – deaktiviert

> **Wichtige**  
> Die Einstellung **DevicePasswordEnabled** muss auf 0 (Gerätekennworts ist aktiviert) festgelegt werden, für die folgenden Richtlinieneinstellungen wirksam werden:
>
> -   AllowSimpleDevicePassword
> -   MinDevicePasswordLength
> -   AlphanumericDevicePasswordRequired
> -   MaxDevicePasswordFailedAttempts
> -   MaxInactivityTimeDeviceLock
> -   MinDevicePasswordComplexCharacters&nbsp;

> **Wichtige**  
> Wenn **DevicePasswordEnabled** auf 0 festgelegt ist (Gerätekennworts ist aktiviert), werden die folgenden Richtlinien festgelegt:
>
> -   MinDevicePasswordLength wird auf 4 festgelegt.
> -   MinDevicePasswordComplexCharacters wird auf 1 festgelegt.
>
> Wenn **DevicePasswordEnabled** auf 1 festgelegt ist (Gerätekennworts deaktiviert ist), und klicken Sie dann die folgenden Richtlinien für DeviceLock auf 0 festgelegt werden:
>
> -   MinDevicePasswordLength
> -   MinDevicePasswordComplexCharacters

 

<a href="" id="devicelock-devicepasswordexpiration"></a>**DeviceLock/DevicePasswordExpiration**  
<p style="margin-left: 20px">Gibt an, wann das Kennwort (in Tagen) abläuft.

> **Hinweis**  Diese Richtlinie muss in einem unteilbare Befehl eingeschlossen werden.


<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   Eine ganze Zahl X, wobei 0 &lt;= X &lt;730 =.
-   0 (Standard) - Kennwörter laufen nicht ab.

<p style="margin-left: 20px">Wenn alle Richtlinienwerte, die = 0 then 0; Andernfalls ist Min Richtlinienwert die sicherste Wert.

<p style="margin-left: 20px">Weitere Informationen zu dieser Richtlinie finden Sie unter [Exchange ActiveSync-Richtlinie Engine Overview](https://technet.microsoft.com/library/dn282287.aspx).

<a href="" id="devicelock-devicepasswordhistory"></a>**DeviceLock/DevicePasswordHistory**  
<p style="margin-left: 20px">Gibt an, wie viele Kennwörter im Verlauf gespeichert werden können, die nicht verwendet werden kann.

> **Hinweis**  Diese Richtlinie muss in einem unteilbare Befehl eingeschlossen werden.


<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   Eine ganze Zahl X, wobei 0 &lt;X = &lt;= 50.
-   0 (Standard)

<p style="margin-left: 20px">Der Wert enthält aktuelles Kennwort des Benutzers ein. Dies bedeutet, dass bei der Einstellung 1 der Benutzer ihr aktuelle Kennwort wiederverwenden ist nicht möglich, wenn ein neues Kennwort ein, während eine Einstellung von 5 bedeutet, dass ein Benutzer auf ihr aktuelles Kennwort oder auf ihre vorherigen vier Kennwörter ihr neue Kennwort festlegen kann nicht auswählen.

<p style="margin-left: 20px">Max-Richtlinienwert ist der am häufigsten beschränkt.

<p style="margin-left: 20px">Weitere Informationen zu dieser Richtlinie finden Sie unter [Exchange ActiveSync-Richtlinie Engine Overview](https://technet.microsoft.com/library/dn282287.aspx).

<a href="" id="devicelock-enforcelockscreenandlogonimage"></a>**DeviceLock/EnforceLockScreenAndLogonImage**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt die Sperre Bildschirm und bei der Anmeldung Standardbild angezeigt, wenn kein Benutzer angemeldet ist an. Außerdem festgelegt, das angegebene Bild für alle Benutzer, die das Standardbild ersetzt. Dasselbe Bild wird für die lock- und die Anmeldung Bildschirme verwendet. Benutzer werden nicht auf dieses Bild ändern können.

> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Pro Enterprise und Bildungseinrichtungen Editionen erzwungen und in Windows 10 Home nicht unterstützt.


<p style="margin-left: 20px">Werttyp ist eine Zeichenfolge, die den vollständigen Bild Filepath und den Dateinamen wird.

<a href="" id="devicelock-enforcelockscreenprovider"></a>**DeviceLock/EnforceLockScreenProvider**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Schränkt Sperren das Bild zu einem bestimmten Sperre Bildschirm Anbieter an. Benutzer können Änderung dieser Anbieter sein.

> **Hinweis**  Mit dieser Richtlinie wird nur für mobile Geräte in Windows 10 erzwungen.


<p style="margin-left: 20px">Werttyp ist eine Zeichenfolge, die die AppID ist.

<a href="" id="devicelock-maxdevicepasswordfailedattempts"></a>**DeviceLock/MaxDevicePasswordFailedAttempts**  
Die Anzahl der Authentifizierungsfehler zulässig sind, bevor das Gerät wird bereinigt werden. Der Wert 0 deaktiviert Gerät Remotegerätzurücksetzung Funktionalität.

> **Hinweis**  Diese Richtlinie muss in einem unteilbare Befehl eingeschlossen werden.


<p style="margin-left: 20px">Diese Richtlinie enthält verschiedene Verhaltensweisen auf dem mobilen Gerät und Desktop.

-   Auf einem mobilen Gerät wenn der Benutzer den Wert festlegen, indem diese Richtlinie erreicht ist dann das Gerät Kennworteingaben gelöscht.
-   Auf einem Desktop Wenn der Benutzer den Wert festlegen, indem diese Richtlinie erreicht ist es nicht mit gelöscht. Stattdessen hört der Desktop auf BitLocker-Wiederherstellungsmodus, wodurch die Daten wiederhergestellt, aber nicht zugegriffen werden. Wenn BitLocker nicht aktiviert ist, kann nicht die Richtlinie angewendet werden.

    Vor dem Erreichen des Grenzwert Versuche der Benutzer wird gesendet, auf dem Sperrbildschirm und darauf hingewiesen, dass mehr Versuche werden ihre Computer sperren. Wenn der Benutzer das Limit erreicht, wird das Gerät automatisch neu gestartet und zeigt die BitLocker-Wiederherstellung-Seite. Auf dieser Seite fordert den Benutzer für die BitLocker-Wiederherstellung-Taste.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   Eine ganze Zahl X wobei 4 &lt;= X &lt;16 für Desktop und 0 = &lt;= X &lt;= 999 für mobile Geräte.
-   0 (Standard) – das Gerät wird nie bereinigt, nachdem eine falsche PIN oder Kennwort eingegeben wird.

<p style="margin-left: 20px">Sicherstes Wert 0 ist, wenn alle Werte = 0; Andernfalls ist Min Richtlinienwert die sicherste Wert.

<p style="margin-left: 20px">Weitere Informationen zu dieser Richtlinie finden Sie unter [Exchange ActiveSync-Richtlinie Engine Overview](https://technet.microsoft.com/library/dn282287.aspx).

<a href="" id="devicelock-maxinactivitytimedevicelock"></a>**DeviceLock/MaxInactivityTimeDeviceLock**  
<p style="margin-left: 20px">Gibt die maximale Zeitdauer (in Minuten) zulässig, nachdem das Gerät, das Gerät zu PIN oder Kennwort gesperrt werden verursachen wird im Leerlauf ist. Benutzer können auswählen, alle vorhandenen Timeout-Wert kleiner als die angegebene maximale Zeit in der app Settings. Hinweis Die Lumia 950 und 950XL haben einen maximale Timeoutwert von 5 Minuten, ungeachtet des Werts, der durch diese Richtlinie festgelegt.

> **Hinweis**  Diese Richtlinie muss in einem unteilbare Befehl eingeschlossen werden.


<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   Eine ganze Zahl X, wobei 0 &lt;X = &lt;= 999.
-   0 (Standard) - kein Timeout definiert ist. "0" wird der Standardwert ist Windows Phone 7.5 Parität und vom interpretiert wird, wie "kein Timeout definiert ist."

<p style="margin-left: 20px">Weitere Informationen zu dieser Richtlinie finden Sie unter [Exchange ActiveSync-Richtlinie Engine Overview](https://technet.microsoft.com/library/dn282287.aspx).

<a href="" id="devicelock-mindevicepasswordcomplexcharacters"></a>**DeviceLock/MinDevicePasswordComplexCharacters**  
<p style="margin-left: 20px">Die Anzahl der komplexe Elementtypen (Groß-und Kleinbuchstaben, Zahlen und Interpunktion) für einen starken PIN oder ein Kennwort erforderlich.

> **Hinweis**  
> Diese Richtlinie muss in einem unteilbare Befehl eingeschlossen werden.
>
> Verwenden Sie immer den Befehl Replace anstelle von hinzufügen für diese Richtlinie in Windows 10 für desktop-Editionen.

<p style="margin-left: 20px">PIN erzwingt das folgende Verhalten für Desktop- und mobile Geräte:

-   1 – nur Ziffern
-   2 - Ziffern und Kleinbuchstaben sind erforderlich
-   3 - Ziffern, Kleinbuchstaben und Großbuchstaben sind erforderlich
-   4 - Ziffern, Kleinbuchstaben, Großbuchstaben und Sonderzeichen sind erforderlich

<p style="margin-left: 20px">Der Standardwert ist 1. In der folgenden Liste sind die unterstützten Werte und erzwungene Istwerte:

<table style="margin-left: 20px">
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Kontotyp</th>
<th>Unterstützte Werte</th>
<th>Erzwungene Istwerte</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>Mobile</p></td>
<td style="vertical-align:top"><p>1,2,3,4</p></td>
<td style="vertical-align:top"><p>Identisch mit der festgelegte Wert</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Desktop lokale Konten</p></td>
<td style="vertical-align:top"><p> 1 2, 3</p></td>
<td style="vertical-align:top"><p>3</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Desktop Microsoft Konten</p></td>
<td style="vertical-align:top"><p>1,2</p></td>
<td style="vertical-align:top"><p2</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Desktop-Domänenkonten</p></td>
<td style="vertical-align:top"><p>Nicht unterstützt</p></td>
<td style="vertical-align:top">Nicht unterstützt</p></td>
</tr>
</tbody>
</table>


<p style="margin-left: 20px">Erzwungene Werte für lokale und Microsoft Accounts:

-   Lokale Konten unterstützen Werte 1, 2 und 3, jedoch sie immer einen Wert von 3 erzwingen.
-   Kennwörter für lokale Konten müssen die folgenden Mindestanforderungen erfüllen:

    -   Keine Kontonamen oder Teile des vollständigen Namen des Benutzers, die zwei aufeinander folgenden Zeichen überschreiten des Benutzers
    -   Mindestens sechs Zeichen lang sein
    -   Enthalten Sie Zeichen aus drei der folgenden vier Kategorien:

        -   Großbuchstaben (A bis Z)
        -   Kleinbuchstaben (a bis Z)
        -   Basis 10 Ziffern (0 bis 9)
        -   Sonderzeichen (!, $, \#, % usw..)

<p style="margin-left: 20px">Die Durchsetzung von Richtlinien für Microsoft Konten auftreten, auf dem Server und der Server erfordert eine Kennwortlänge von 8 und eine Komplexität von 2. Komplexität der Wert 3 oder 4 wird nicht unterstützt, und Microsoft Konten nicht kompatible macht Festlegen dieses Werts auf dem Server.

<p style="margin-left: 20px">Weitere Informationen zu dieser Richtlinie finden Sie unter [Engine-Übersicht über Exchange ActiveSync-Richtlinie](https://technet.microsoft.com/library/dn282287.aspx) und [Knowledge Base-Artikel](https://support.office.com/article/This-device-doesn-t-meet-the-security-requirements-set-by-your-email-administrator-87132fc7-2c7f-4a71-9de0-779ff81c86ca).

<a href="" id="devicelock-mindevicepasswordlength"></a>**DeviceLock/MinDevicePasswordLength**  
<p style="margin-left: 20px">Gibt die Mindestanzahl oder Zeichen in der PIN oder das Kennwort erforderlich.

> **Hinweis**  
> Diese Richtlinie muss in einem unteilbare Befehl eingeschlossen werden.
>
> Verwenden Sie immer den Befehl Replace anstelle von hinzufügen für diese Richtlinie in Windows 10 für desktop-Editionen.


<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   Eine ganze Zahl X wobei 4 &lt;X = &lt;= 16 für mobile Geräte und Desktops. Lokale Konten werden jedoch immer eine minimale Kennwortlänge von 6 erzwingen.
-   Nicht erzwungen.
-   Der Standardwert ist 4 für mobile Geräte und Desktopgeräte.

<p style="margin-left: 20px">Max-Richtlinienwert ist der am häufigsten beschränkt.

<p style="margin-left: 20px">Weitere Informationen zu dieser Richtlinie finden Sie unter [Engine-Übersicht über Exchange ActiveSync-Richtlinie](https://technet.microsoft.com/library/dn282287.aspx) und [Knowledge Base-Artikel](https://support.office.com/article/This-device-doesn-t-meet-the-security-requirements-set-by-your-email-administrator-87132fc7-2c7f-4a71-9de0-779ff81c86ca).

<a href="" id="devicelock-screentimeoutwhilelocked"></a>**DeviceLock/ScreenTimeoutWhileLocked**   
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Mobile erzwungen und im Windows-10 für Desktop nicht unterstützt.

 

<p style="margin-left: 20px">Ermöglicht es Unternehmen, legen Sie die Dauer in Sekunden für den Timeout Bildschirm klicken Sie auf dem Sperrbildschirm Windows 10 Mobile Geräte.

<p style="margin-left: 20px">Unterstützte Mindestwert ist 10.

<p style="margin-left: 20px">Unterstützte Höchstwert ist 1800.

<p style="margin-left: 20px">Der Standardwert ist 10.

<a href="" id="experience-allowcopypaste"></a>**Erfahrung/AllowCopyPaste**   
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Mobile erzwungen und im Windows-10 für Desktop nicht unterstützt.


<p style="margin-left: 20px">Gibt an, ob kopieren und Einfügen ist zulässig.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="experience-allowcortana"></a>**Erfahrung/AllowCortana**  
<p style="margin-left: 20px">Gibt an, ob auf dem Gerät Cortana zulässig ist. Wenn Sie aktivieren oder konfigurieren Sie diese Einstellung nicht, ist auf dem Gerät Cortana zulässig. Wenn Sie diese Einstellung deaktivieren, ist Cortana deaktiviert. Wenn Cortana deaktiviert ist, werden Benutzer weiterhin suchen verwenden, um die Elemente auf dem Gerät zu finden sein.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="experience-allowdevicediscovery"></a>**Erfahrung/AllowDeviceDiscovery**  
<p style="margin-left: 20px">Ermöglicht es Benutzern, aktivieren/deaktivieren Gerät Discovery UX.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Bei Festlegung auf 0, der Projektion Bereich deaktiviert ist. Die Win + P und Win + K Tastenkombinationen funktionieren nicht auf.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="experience-allowmanualmdmunenrollment"></a>**Erfahrung/AllowManualMDMUnenrollment**  
<p style="margin-left: 20px">Gibt an, ob der Benutzer das Jahrestag-Konto mithilfe der Jahrestag-Systemsteuerung löschen kann.

> **Hinweis**  Der Server MDM kann immer Remote das Konto löschen.


<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="experience-allowscreencapture"></a>**Erfahrung/AllowScreenCapture**   
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Mobile erzwungen und im Windows-10 für Desktop nicht unterstützt.


<p style="margin-left: 20px">Gibt an, ob die Bildschirmaufnahme zulässig ist.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="experience-allowsimerrordialogpromptwhennosim"></a>**Erfahrung/AllowSIMErrorDialogPromptWhenNoSIM**   
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Mobile erzwungen und im Windows-10 für Desktop nicht unterstützt.


<p style="margin-left: 20px">Gibt an, ob ein Dialogfeld angezeigt wird, wenn keine SIM-Karte erkannt wird.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – wird SIM Karte Dialogfeld Aufforderung nicht angezeigt.
-   1 (Standard) – SIM Karte Dialogfeld angezeigt.

<a href="" id="experience-allowsyncmysettings"></a>**Erfahrung/AllowSyncMySettings**  
<p style="margin-left: 20px">Zugelassen oder verweigert alle Windows Sync-Einstellungen auf dem Gerät. Informationen dazu, welche Einstellungen sync'ed sind finden Sie unter [About Sync-Einstellung auf Windows-10-Geräten](http://windows.microsoft.com/windows-10/about-sync-settings-on-windows-10-devices).

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Sync-Einstellungen ist nicht zulässig.
-   1 (Standard) – Sync-Einstellungen zulässig.

<a href="" id="experience-allowtaskswitcher"></a>**Erfahrung/AllowTaskSwitcher**  
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Mobile erzwungen und im Windows-10 für Desktop nicht unterstützt.


<p style="margin-left: 20px">Zugelassen oder verweigert Aufgabe auf dem Gerät wechseln.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Umschalten zwischen den Aufgaben ist nicht zulässig.
-   1 (Standard) – zulässig Aufgabe zu wechseln.

<a href="" id="experience-allowthirdpartysuggestionsinwindowsspotlight"></a>**Erfahrung/AllowThirdPartySuggestionsInWindowsSpotlight**  
> **Hinweis**  Diese Richtlinie ist nur für Windows 10 Pro, Windows 10 Enterprise und Windows 10 Education verfügbar.


<p style="margin-left: 20px">Gibt an, ob die app und Inhalte Vorschläge aus Software von Drittanbietern zu spotlight Herausgeber in Windows-Features wie Sperre Bildschirm Spotlight, vorgeschlagenen apps im Startmenü und Tipps für Windows. Benutzer sehen möglicherweise noch Vorschläge für Features, apps und Dienste von Microsoft.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Drittanbieter-Vorschläge nicht zulässig.
-   1 (Standard) – Drittanbieter-Vorschläge zulässig.

<a href="" id="experience-allowvoicerecording"></a>**Erfahrung/AllowVoiceRecording**  
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Mobile erzwungen und im Windows-10 für Desktop nicht unterstützt.


<p style="margin-left: 20px">Gibt an, ob VoIP-Aufzeichnung für apps zulässig ist.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="experience-allowwindowsconsumerfeatures"></a>**Erfahrung/AllowWindowsConsumerFeatures**   
> **Hinweis**  Diese Richtlinie ist nur für Desktop in Windows 10 erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">Mit dieser Richtlinie können IT-Administratoren Erfahrungen aktivieren, die in der Regel für Verbraucher nur, wie etwa Start Vorschläge, Mitgliedschaft Benachrichtigungen werden, Post-OOBE app installieren und Kacheln umleiten.

> **Wichtige**  
> Dieser Knoten muss über den folgenden Pfad zugegriffen werden:
>
> -   **./User/Vendor/MSFT/Policy/Config/Experience/AllowWindowsConsumerFeatures** zum Festlegen der Richtlinie.
> -   **./User/Vendor/MSFT/Policy/Result/Experience/AllowWindowsConsumerFeatures** , um das Ergebnis zu erzielen.

 
<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 – zulässig.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="experience-allowwindowsspotlight"></a>**Erfahrung/AllowWindowsSpotlight**   
> **Hinweis**  Diese Richtlinie ist nur für Windows 10 Enterprise und Windows 10 Education verfügbar.


<p style="margin-left: 20px">Gibt an, ob alle Fenster deaktivieren gleichzeitig Features spotlight. Wenn Sie diese Einstellung aktivieren, Windows spotlight auf Sperre Bildschirm Tipps für Windows, Microsoft Consumer Features und andere zugehörige Features deaktiviert. Sie sollten diese richtlinieneinstellung aktivieren, wenn Ihr Ziel besteht darin, die Minimierung des Netzwerkverkehrs von Zielgeräten. Wenn Sie deaktivieren oder diese Einstellung nicht konfigurieren, wird Windows Spotlight Features sind zulässig und einzeln über ihrer Richtlinieneinstellungen für die entsprechende gesteuert werden können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="experience-allowwindowstips"></a>**Erfahrung/AllowWindowsTips**  
Aktiviert oder deaktiviert die Tipps für Windows / weiche Zielseite.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – deaktiviert.
-   1 (Standard) – aktiviert.

<a href="" id="experience-configurewindowsspotlightonlockscreen"></a>**Erfahrung/ConfigureWindowsSpotlightOnLockScreen**  
> **Hinweis**  Diese Richtlinie ist nur für Windows 10 Enterprise und Windows 10 Education verfügbar.


<p style="margin-left: 20px">Ermöglicht es IT-Administratoren geben an, ob auf dem Bildschirm des Benutzers Sperre Spotlight verwendet werden soll. Wenn eine Enterprise Content Service spotlight in Ihrer Organisation nicht vorhanden ist, wird diese Richtlinie als Einstellung der 1 dasselbe Verhalten.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – none.
-   1 (Standard) – Windows Spotlight aktiviert.
-   2 – Platzhalter nur für zukünftige Erweiterungen. Mithilfe dieses Werts hat keine Auswirkung.

<a href="" id="experience-donotshowfeedbacknotifications"></a>**Erfahrung/DoNotShowFeedbackNotifications**  
<p style="margin-left: 20px">Verhindert, dass Geräte mit Feedback Fragen von Microsoft.

<p style="margin-left: 20px">Wenn Sie diese Einstellung aktivieren, sehen die Benutzer nicht mehr Feedback Benachrichtigungen über die Feedback Hub app. Wenn Sie deaktivieren oder diese Einstellung nicht konfigurieren, können Benutzer Benachrichtigungen über die Frage Feedback Hub app-Benutzer für Feedback angezeigt.

<p style="margin-left: 20px">Wenn Sie deaktivieren oder diese Einstellung nicht konfigurieren, können Benutzer steuern, wie oft sie Feedback Fragen erhalten.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – Feedback Benachrichtigungen nicht deaktiviert sind. Der aktuelle Zustand des Feedback Benachrichtigungen auf dem Gerät hängt dann was GP konfiguriert hat oder was der Benutzer lokal konfiguriert hat.
-   1 – Feedback Benachrichtigungen werden deaktiviert.

<a href="" id="licensing-allowwindowsentitlementreactivation"></a>**Lizenzierung/AllowWindowsEntitlementReactivation**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Aktiviert oder deaktiviert Windows Lizenz Reaktivierung auf verwalteten Geräten.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Windows deaktivieren Lizenz Reaktivierung auf verwalteten Geräten.
-   1 (Standard) – Windows aktivieren Lizenz Reaktivierung auf verwalteten Geräten.

<a href="" id="licensing-disallowkmsclientonlineavsvalidation"></a>**Lizenzierung/DisallowKMSClientOnlineAVSValidation**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Durch Aktivieren dieser Einstellung wird verhindert, dass diese Computer Senden von Daten an Microsoft zu im Zusammenhang mit den Aktivierungsstatus.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – deaktiviert.
-   1 – aktiviert.

<a href="" id="lockdown-allowedgeswipe"></a>**Sperren/AllowEdgeSwipe**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Ermöglicht es dem Benutzer alle System-Benutzeroberfläche durch ein Lesegerät aus jeder Bildschirmrand per Fingereingabe aufrufen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 - nicht zulassen, führen Sie eine streifbewegung Kante.
-   1 (standardmäßig nicht konfiguriert) - zulassen, führen Sie eine streifbewegung Kante.

<p style="margin-left: 20px">Die einfachste Möglichkeit, überprüfen Sie, ob die Richtlinie wird im Explorer-Prozess neu starten oder neu starten, nachdem die Richtlinie angewendet wird. Und versuchen Sie es dann vom rechten Rand des Bildschirms führen. Das gewünschte Ergebnis wird für die Action-Center nicht durch die führen Sie eine streifbewegung aufgerufen werden. Sie können auch geben ein Tablet-Modus und versuchen, führen Sie im oberen Bereich des Bildschirms zum neu anordnen. Wird auch deaktiviert werden.

<a href="" id="maps-enableofflinemapsautoupdate"></a>**Karten/EnableOfflineMapsAutoUpdate**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Deaktiviert das automatische Herunterladen und Aktualisierung von Zuordnungsdaten.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   65535 (Standard) – nicht konfiguriert. Auswahl des Benutzers.
-   0 – deaktiviert. Deaktiviert die automatische Aktualisierung zu erzwingen.
-   1 – aktiviert. Klicken Sie auf automatische Aktualisierung zu erzwingen.

<p style="margin-left: 20px">Nachdem die Richtlinie angewendet wird, können Sie sicherstellen, dass die Einstellungen in der Benutzeroberfläche im **System** &gt; **Offline Maps**.

<a href="" id="maps-allowofflinemapsdownloadovermeteredconnection"></a>**Karten/AllowOfflineMapsDownloadOverMeteredConnection**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Ermöglicht das Herunterladen und die Aktualisierung von Zuordnungsdaten über getaktete Verbindungen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   65535 (Standard) – nicht konfiguriert. Auswahl des Benutzers.
-   0 – deaktiviert. Force automatisch aktualisieren über getaktete Verbindung zu deaktivieren.
-   1 – aktiviert. Force automatisch aktualisieren über getaktete Verbindung aktivieren.

<p style="margin-left: 20px">Nachdem die Richtlinie angewendet wird, können Sie sicherstellen, dass die Einstellungen in der Benutzeroberfläche im **System** &gt; **Offline Maps**.

<a href="" id="messaging-allowmessagesync"></a>**Messaging/AllowMessageSync**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Ermöglicht Textnachricht sichern und Wiederherstellen und Messaging überall. Diese Richtlinie ermöglicht eine Organisation, um diese Features zur Vermeidung von Daten auf Servern außerhalb ihrer Steuerelement zu deaktivieren.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 - Nachricht Sync ist nicht zulässig, und es kann nicht vom Benutzer geändert werden.
-   1 - Message Sync ist zulässig. Der Benutzer kann diese Einstellung ändern.

<a href="" id="networkisolation-enterprisecloudresources"></a>**NetworkIsolation/EnterpriseCloudResources**  
<p style="margin-left: 20px">Enthält eine Liste von Enterprise-Ressourcendomänen gehostet in der Cloud ein, die geschützt werden müssen. Verbindungen mit dieser Ressourcen gelten als Enterprise-Daten. Wenn Sie ein Proxy mit einer Cloud-Ressource verbunden ist, werden über das Unternehmensnetzwerk über den bezeichnet Proxyserver (Port 80)-Datenverkehr an die Cloud-Ressource weitergeleitet. Mit der Richtlinie **EnterpriseInternalProxyServers** muss auch ein Proxy-Server für diesen Zweck verwendet konfiguriert sein. Diese Domänenliste ist eine Pipe getrennte Liste von Cloudressourcen. Jede Ressource Cloud kann auch optional mit einem internen Proxy-Server kombiniert werden mit einem nachstehenden Komma, gefolgt von der Proxyadresse. Beispielsweise * *&lt;*Cloudresource*&gt;|&lt;*Cloudresource*&gt;|&lt;*Cloudresource*&gt;,&lt;*Proxy*&gt;|&lt;*Cloudresource*&gt;|&lt;*Cloudresource*&gt;,&lt;*Proxy*&gt;| **.

<a href="" id="networkisolation-enterpriseinternalproxyservers"></a>**NetworkIsolation/EnterpriseInternalProxyServers**  
<p style="margin-left: 20px">Dies ist die durch Trennzeichen getrennte Liste der internen Proxy-Server. Zum Beispiel "157.54.14.28, 157.54.11.118, 10.202.14.167, 157.53.14.163, 157.69.210.59". Diese Proxys wurden durch den der Administrator für die Verbindung auf bestimmte Ressourcen im Internet konfiguriert. Sie sind als betrachtet Enterprise Netzwerkadressen. Die Proxys sind nur in Konfigurieren der Richtlinie **EnterpriseCloudResources** , um Datenverkehr an die übereinstimmenden Cloudressourcen über diese Proxys erzwingen genutzt.

<a href="" id="networkisolation-enterpriseiprange"></a>**NetworkIsolation/EnterpriseIPRange**  
<p style="margin-left: 20px">Legt das Unternehmen IP-Adressbereichen an, die der Computer im Unternehmensnetzwerk zu definieren. Daten, die von den Computern, kommt werden als Teil des Unternehmens und geschützt. Diese Speicherorte gilt ein sicherer Ziel für die Enterprise-Daten auf freigegeben werden. Dies ist eine durch Trennzeichen getrennte Liste von Bereichen für IPv4 und IPv6. Beispiel:

``` syntax
10.0.0.0-10.255.255.255,157.54.0.0-157.54.255.255,
192.168.0.0-192.168.255.255,2001:4898::-2001:4898:7fff:ffff:ffff:ffff:ffff:ffff,
2001:4898:dc05::-2001:4898:dc05:ffff:ffff:ffff:ffff:ffff,
2a01:110::-2a01:110:7fff:ffff:ffff:ffff:ffff:ffff,
fd00::-fdff:ffff:ffff:ffff:ffff:ffff:ffff:ffff
       
```

<a href="" id="networkisolation-enterpriseiprangesareauthoritative"></a>**NetworkIsolation/EnterpriseIPRangesAreAuthoritative**  
<p style="margin-left: 20px">Boolescher Wert, der dem Client konfigurierte Liste akzeptiert und nicht zum Heuristik verwenden, um andere Subnetze suchen mitteilt.

<a href="" id="networkisolation-enterprisenetworkdomainnames"></a>**NetworkIsolation/EnterpriseNetworkDomainNames**  
<p style="margin-left: 20px">Dies ist die Liste der Domänen, die die Grenzen des Unternehmens umfassen. Daten von einem diese Domänen, die zu einem Gerät gesendet wird als Enterprise-Daten und geschützt werden diese Speicherorte berücksichtigt werden ein sicherer Ziel für die Enterprise-Daten auf freigegeben werden. Dies ist eine durch Trennzeichen getrennte Liste der Domänen, beispielsweise "contoso.sharepoint.com, Fabrikam.com".

> **Hinweis**  Der Client erfordert Domänennamen ein, um die kanonische werden, andernfalls wird die Einstellung vom Client zurückgewiesen.
 

<p style="margin-left: 20px">Hier werden die Schritte zum Erstellen von kanonische Domänennamen:

1.  Umwandeln Sie die ASCII-Zeichen (nur A – Z) in Kleinbuchstaben. Beispielsweise Microsoft.COM -&gt; microsoft.com.
2.  Rufen Sie [IdnToAscii](https://msdn.microsoft.com/library/windows/desktop/dd318149.aspx) mit IDN\_VERWENDUNG\_STD3\_ASCII\_REGELN wie die Kennzeichen.
3.  Anruf [IdnToUnicode](https://msdn.microsoft.com/library/windows/desktop/dd318151.aspx) ohne Kennzeichen Set (DwFlags = 0).

<a href="" id="networkisolation-enterpriseproxyservers"></a>**NetworkIsolation/EnterpriseProxyServers**  
<p style="margin-left: 20px">Dies ist eine durch Trennzeichen getrennte Liste der Proxy-Server. Alle Server in dieser Liste gilt als nicht-Enterprise. Zum Beispiel "157.54.14.28, 157.54.11.118, 10.202.14.167, 157.53.14.163, 157.69.210.59".

<a href="" id="networkisolation-enterpriseproxyserversareauthoritative"></a>**NetworkIsolation/EnterpriseProxyServersAreAuthoritative**  
<p style="margin-left: 20px">Boolescher Wert, der den Client die konfigurierte Liste der Proxys und nicht Try zum Erkennen von anderen Proxys Arbeit akzeptieren weist.

<a href="" id="networkisolation-neutralresources"></a>**NetworkIsolation/NeutralResources**  
<p style="margin-left: 20px">Liste der Domänennamen, die für die Arbeit "oder" Persönliche Ressource verwendet werden können.

<a href="" id="notifications-disallownotificationmirroring"></a>**Benachrichtigungen/DisallowNotificationMirroring**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Boolescher Wert, der Spiegelung Benachrichtigung deaktiviert.

<p style="margin-left: 20px">Für jeden Benutzer, an dem Gerät angemeldet Wenn Sie diese Richtlinie (Set-Wert auf 1) aktivieren werden die app und System Benachrichtigungen von diesem Benutzer auf diesem Gerät empfangen nicht auf andere Geräte der gleichen angemeldeten Benutzer gespiegelt erhalten möchten. Wenn Sie diese Richtlinie (festgelegter Wert auf 0) nicht konfigurieren oder deaktivieren werden die Benachrichtigungen von diesem Benutzer auf diesem Gerät empfangen auf anderen Geräten der gleichen angemeldeten Benutzer gespiegelt werden. Dieses Feature kann durch apps deaktiviert werden, die keine Benachrichtigung Spiegelung teilnehmen möchten. Dieses Feature kann auch durch den Benutzer in der Seite Cortana deaktiviert werden.

<p style="margin-left: 20px">Es ist kein Neustart oder Dienst Neustart erforderlich, damit diese Richtlinie wirksam wird.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – deaktivieren Sie die Spiegelung der Benachrichtigung.
-   1 – Aktivieren Sie Benachrichtigung Spiegelung.

<a href="" id="privacy-allowautoacceptpairingandprivacyconsentprompts"></a>**Datenschutz/AllowAutoAcceptPairingAndPrivacyConsentPrompts**  
<p style="margin-left: 20px">Ermöglicht oder deaktiviert die automatische Annahme das Dialogfeld eine Kopplung und private Benutzer Zustimmung beim Starten von apps.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – nicht zugelassen.
-   1 – zulässig.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="privacy-allowinputpersonalization"></a>**Datenschutz/AllowInputPersonalization**  
<p style="margin-left: 20px">Oder keinen ermöglicht die Eingabe von personenbezogene Informationen Geräte entfernt oder lokal (Cortana, Eingabe, Freihand, Sprache, Dictation usw.) speichern.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

> **Hinweis**  In der aktuellen Version von Windows 10 Mobile entfernt Wenn diese Richtlinie auf 0 nicht die Liste mit Kontaktnamen auf dem Gerät aus der Liste der Kandidaten eingegeben. Dieses Problem wird in einer zukünftigen Version behoben werden.

 

<a href="" id="privacy-disableadvertisingid"></a>**Datenschutz/DisableAdvertisingId**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Aktiviert oder deaktiviert die Werbung-ID.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – deaktiviert.
-   1 – aktiviert.
-   65535 (Standard) – nicht konfiguriert.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="privacy-letappsaccessaccountinfo"></a>**Datenschutz/LetAppsAccessAccountInfo**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt an, ob Windows apps Kontoinformationen zugreifen können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Benutzer im Steuerelement.
-   1 – Force ermöglichen.
-   2 - Force verweigern.

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 2.

<a href="" id="privacy-letappsaccessaccountinfo-forceallowtheseapps"></a>**Datenschutz/LetAppsAccessAccountInfo\_ForceAllowTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennte Paket Kategorienamen des Windows-apps. Aufgeführten Windows-apps werden auf Kontoinformationen zugreifen. Diese Einstellung überschreibt die Einstellung LetAppsAccessAccountInfo Standard für die angegebenen Windows-apps.

<a href="" id="privacy-letappsaccessaccountinfo-forcedenytheseapps"></a>**Datenschutz/LetAppsAccessAccountInfo\_ForceDenyTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennte Paket Kategorienamen des Windows-apps. Aufgeführten Windows-apps können nicht auf den Zugriff auf Kontoinformationen. Diese Einstellung überschreibt die Einstellung LetAppsAccessAccountInfo Standard für die angegebenen Windows-apps.

<a href="" id="privacy-letappsaccessaccountinfo-userincontroloftheseapps"></a>**Datenschutz/LetAppsAccessAccountInfo\_UserInControlOfTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennte Paket Kategorienamen des Windows-apps. Der Benutzer kann die Konto Informationen den Datenschutz für die aufgeführten Windows-apps zu steuern. Diese Einstellung überschreibt die Einstellung LetAppsAccessAccountInfo Standard für die angegebenen Windows-apps.

<a href="" id="privacy-letappsaccesscalendar"></a>**Datenschutz/LetAppsAccessCalendar**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt an, ob den Kalender auf apps für Windows zugreifen können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Benutzer im Steuerelement.
-   1 – Force ermöglichen.
-   2 - Force verweigern.

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 2.

<a href="" id="privacy-letappsaccesscalendar-forceallowtheseapps"></a>**Datenschutz/LetAppsAccessCalendar\_ForceAllowTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennte Paket Kategorienamen des Windows-apps. Aufgeführten Windows apps dürfen Zugriff auf den Kalender. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessCalendar für die angegebenen Windows-apps.

<a href="" id="privacy-letappsaccesscalendar-forcedenytheseapps"></a>**Datenschutz/LetAppsAccessCalendar\_ForceDenyTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennte Paket Kategorienamen des Windows-apps. Aufgeführten Windows-apps können nicht auf den Zugriff auf den Kalender. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessCalendar für die angegebenen Windows-apps.

<a href="" id="privacy-letappsaccesscalendar-userincontroloftheseapps"></a>**Datenschutz/LetAppsAccessCalendar\_UserInControlOfTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennte Paket Kategorienamen des Windows-apps. Der Benutzer kann die Kalender für den Datenschutz für die aufgeführten Windows-apps zu steuern. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessCalendar für die angegebenen Windows-apps.

<a href="" id="privacy-letappsaccesscallhistory"></a>**Datenschutz/LetAppsAccessCallHistory**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt an, ob Windows apps Anrufliste zugreifen können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Benutzer im Steuerelement.
-   1 – Force ermöglichen.
-   2 - Force verweigern.

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 2.

<a href="" id="privacy-letappsaccesscallhistory-forceallowtheseapps"></a>**Datenschutz/LetAppsAccessCallHistory\_ForceAllowTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennte Paket Kategorienamen des Windows-apps. Aufgeführten Windows apps dürfen Zugriff auf Verlauf aufrufen. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessCallHistory für die angegebenen Windows-apps.

<a href="" id="privacy-letappsaccesscallhistory-forcedenytheseapps"></a>**Datenschutz/LetAppsAccessCallHistory\_ForceDenyTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennte Paket Kategorienamen des Windows-apps. Aufgeführten Windows-apps werden keinen Zugriff auf Verlauf aufrufen. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessCallHistory für die angegebenen Windows-apps.

<a href="" id="privacy-letappsaccesscallhistory-userincontroloftheseapps"></a>**Datenschutz/LetAppsAccessCallHistory\_UserInControlOfTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennte Paket Kategorienamen des Windows-apps. Der Benutzer kann die Anruf Verlauf den Datenschutz für die aufgeführten Windows-apps zu steuern. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessCallHistory für die angegebenen Windows-apps.

<a href="" id="privacy-letappsaccesscamera"></a>**Datenschutz/LetAppsAccessCamera**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt an, ob die Kamera auf apps für Windows zugreifen können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Benutzer im Steuerelement.
-   1 – Force ermöglichen.
-   2 - Force verweigern.

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 2.

<a href="" id="privacy-letappsaccesscamera-forceallowtheseapps"></a>**Datenschutz/LetAppsAccessCamera\_ForceAllowTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführte apps dürfen Zugriff auf die Kamera. Diese Einstellung überschreibt die Einstellung LetAppsAccessCamera Standard für die angegebenen apps.

<a href="" id="privacy-letappsaccesscamera-forcedenytheseapps"></a>**Datenschutz/LetAppsAccessCamera\_ForceDenyTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführten apps werden der Zugriff auf die Kamera verweigert. Diese Einstellung überschreibt die Einstellung LetAppsAccessCamera Standard für die angegebenen apps.

<a href="" id="privacy-letappsaccesscamera-userincontroloftheseapps"></a>**Datenschutz/LetAppsAccessCamera\_UserInControlOfTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Der Benutzer kann die Kamera für den Datenschutz für aufgeführte apps zu steuern. Diese Einstellung überschreibt die Einstellung LetAppsAccessCamera Standard für die angegebenen apps.

<a href="" id="privacy-letappsaccesscontacts"></a>**Datenschutz/LetAppsAccessContacts**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt an, ob Windows apps Kontakte zugreifen können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Benutzer im Steuerelement.
-   1 – Force ermöglichen.
-   2 - Force verweigern.

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 2.

<a href="" id="privacy-letappsaccesscontacts-forceallowtheseapps"></a>**Datenschutz/LetAppsAccessContacts\_ForceAllowTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführten apps dürfen Zugriff auf Kontakte. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessContacts für die angegebene apps.

<a href="" id="privacy-letappsaccesscontacts-forcedenytheseapps"></a>**Datenschutz/LetAppsAccessContacts\_ForceDenyTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführten apps sind Zugriff auf Kontakte. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessContacts für die angegebene apps.

<a href="" id="privacy-letappsaccesscontacts-userincontroloftheseapps"></a>**Datenschutz/LetAppsAccessContacts\_UserInControlOfTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Der Benutzer kann die Kontakte für den Datenschutz für die aufgeführten apps zu steuern. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessContacts für die angegebene apps.

<a href="" id="privacy-letappsaccessemail"></a>**Datenschutz/LetAppsAccessEmail**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt an, ob Windows apps auf e-Mails zugreifen können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Benutzer im Steuerelement.
-   1 – Force ermöglichen.
-   2 - Force verweigern.

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 2.

<a href="" id="privacy-letappsaccessemail-forceallowtheseapps"></a>**Datenschutz/LetAppsAccessEmail\_ForceAllowTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführte apps dürfen Zugriff auf e-Mail. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessEmail für die angegebene apps.

<a href="" id="privacy-letappsaccessemail-forcedenytheseapps"></a>**Datenschutz/LetAppsAccessEmail\_ForceDenyTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführten apps sind Zugriff auf e-Mail. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessEmail für die angegebene apps.

<a href="" id="privacy-letappsaccessemail-userincontroloftheseapps"></a>**Datenschutz/LetAppsAccessEmail\_UserInControlOfTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Der Benutzer kann die e-Mail für den Datenschutz für die aufgeführten apps zu steuern. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessEmail für die angegebene apps.

<a href="" id="privacy-letappsaccesslocation"></a>**Datenschutz/LetAppsAccessLocation**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt an, ob Windows apps Speicherort zugreifen können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Benutzer im Steuerelement.
-   1 – Force ermöglichen.
-   2 - Force verweigern.

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 2.

<a href="" id="privacy-letappsaccesslocation-forceallowtheseapps"></a>**Datenschutz/LetAppsAccessLocation\_ForceAllowTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführten apps dürfen Zugriff auf den Standort. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessLocation für die angegebene apps.

<a href="" id="privacy-letappsaccesslocation-forcedenytheseapps"></a>**Datenschutz/LetAppsAccessLocation\_ForceDenyTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführte apps können nicht auf den Zugriff auf den Standort. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessLocation für die angegebene apps.

<a href="" id="privacy-letappsaccesslocation-userincontroloftheseapps"></a>**Datenschutz/LetAppsAccessLocation\_UserInControlOfTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Der Benutzer ist die Speicherort für den Datenschutz für die aufgeführten apps zu steuern. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessLocation für die angegebene apps.

<a href="" id="privacy-letappsaccessmessaging"></a>**Datenschutz/LetAppsAccessMessaging**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt an, ob Windows-apps können lesen oder Senden von Nachrichten (Text oder MMS).

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Benutzer im Steuerelement.
-   1 – Force ermöglichen.
-   2 - Force verweigern.

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 2.

<a href="" id="privacy-letappsaccessmessaging-forceallowtheseapps"></a>**Datenschutz/LetAppsAccessMessaging\_ForceAllowTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführte apps dürfen zu lesen oder Senden von Nachrichten (Text oder MMS). Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessMessaging für die angegebene apps.

<a href="" id="privacy-letappsaccessmessaging-forcedenytheseapps"></a>**Datenschutz/LetAppsAccessMessaging\_ForceDenyTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführte apps dürfen nicht zum Lesen oder Senden von Nachrichten (Text oder MMS). Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessMessaging für die angegebene apps.

<a href="" id="privacy-letappsaccessmessaging-userincontroloftheseapps"></a>**Datenschutz/LetAppsAccessMessaging\_UserInControlOfTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Der Benutzer kann die messaging für den Datenschutz für die aufgeführten apps zu steuern. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessMessaging für die angegebene apps.

<a href="" id="privacy-letappsaccessmicrophone"></a>**Datenschutz/LetAppsAccessMicrophone**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt an, ob das Mikrofon auf Windows-apps zugreifen können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Benutzer im Steuerelement.
-   1 – Force ermöglichen.
-   2 - Force verweigern.

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 2.

<a href="" id="privacy-letappsaccessmicrophone-forceallowtheseapps"></a>**Datenschutz/LetAppsAccessMicrophone\_ForceAllowTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführten apps dürfen Zugriff auf das Mikrofon. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessMicrophone für die angegebene apps.

<a href="" id="privacy-letappsaccessmicrophone-forcedenytheseapps"></a>**Datenschutz/LetAppsAccessMicrophone\_ForceDenyTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführten apps sind Zugriff auf das Mikrofon. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessMicrophone für die angegebene apps.

<a href="" id="privacy-letappsaccessmicrophone-userincontroloftheseapps"></a>**Datenschutz/LetAppsAccessMicrophone\_UserInControlOfTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Der Benutzer kann die Mikrofon für den Datenschutz für aufgeführte apps zu steuern. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessMicrophone für die angegebene apps.

<a href="" id="privacy-letappsaccessmotion"></a>**Datenschutz/LetAppsAccessMotion**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt an, ob Windows apps Motion Daten zugreifen können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Benutzer im Steuerelement.
-   1 – Force ermöglichen.
-   2 - Force verweigern.

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 2.

<a href="" id="privacy-letappsaccessmotion-forceallowtheseapps"></a>**Datenschutz/LetAppsAccessMotion\_ForceAllowTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführten apps dürfen Zugriff auf Motion-Daten. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessMotion für die angegebene apps.

<a href="" id="privacy-letappsaccessmotion-forcedenytheseapps"></a>**Datenschutz/LetAppsAccessMotion\_ForceDenyTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführten apps sind Zugriff auf Bewegung Daten. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessMotion für die angegebene apps.

<a href="" id="privacy-letappsaccessmotion-userincontroloftheseapps"></a>**Datenschutz/LetAppsAccessMotion\_UserInControlOfTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Der Benutzer kann die Bewegung für den Datenschutz für die aufgeführten apps zu steuern. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessMotion für die angegebene apps.

<a href="" id="privacy-letappsaccessnotifications"></a>**Datenschutz/LetAppsAccessNotifications**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt an, ob Windows apps Benachrichtigungen zugreifen können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Benutzer im Steuerelement.
-   1 – Force ermöglichen.
-   2 - Force verweigern.

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 2.

<a href="" id="privacy-letappsaccessnotifications-forceallowtheseapps"></a>**Datenschutz/LetAppsAccessNotifications\_ForceAllowTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführten apps dürfen Zugriff auf Benachrichtigungen. Diese Einstellung überschreibt die Einstellung LetAppsAccessNotifications Standard für die angegebenen apps.

<a href="" id="privacy-letappsaccessnotifications-forcedenytheseapps"></a>**Datenschutz/LetAppsAccessNotifications\_ForceDenyTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführten apps sind Zugriff auf Benachrichtigungen. Diese Einstellung überschreibt die Einstellung LetAppsAccessNotifications Standard für die angegebenen apps.

<a href="" id="privacy-letappsaccessnotifications-userincontroloftheseapps"></a>**Datenschutz/LetAppsAccessNotifications\_UserInControlOfTheseApps**   
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Der Benutzer kann die Benachrichtigungen über den Datenschutz für die aufgeführten apps zu steuern. Diese Einstellung überschreibt die Einstellung LetAppsAccessNotifications Standard für die angegebenen apps.

<a href="" id="privacy-letappsaccessphone"></a>**Datenschutz/LetAppsAccessPhone**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt an, ob Windows apps Telefonanrufe tätigen können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Benutzer im Steuerelement.
-   1 – Force ermöglichen.
-   2 - Force verweigern.

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 2.

<a href="" id="privacy-letappsaccessphone-forceallowtheseapps"></a>**Datenschutz/LetAppsAccessPhone\_ForceAllowTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführten apps Telefonanrufe tätigen dürfen. Diese Einstellung überschreibt die Einstellung LetAppsAccessPhone Standard für die angegebenen apps.

<a href="" id="privacy-letappsaccessphone-forcedenytheseapps"></a>**Datenschutz/LetAppsAccessPhone\_ForceDenyTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführten apps dürfen keine Telefonanrufe tätigen. Diese Einstellung überschreibt die Einstellung LetAppsAccessPhone Standard für die angegebenen apps.

<a href="" id="privacy-letappsaccessphone-userincontroloftheseapps"></a>**Datenschutz/LetAppsAccessPhone\_UserInControlOfTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Der Benutzer kann die Anruf für den Datenschutz für die aufgeführten apps zu steuern. Diese Einstellung überschreibt die Einstellung LetAppsAccessPhone Standard für die angegebenen apps.

<a href="" id="privacy-letappsaccessradios"></a>**Datenschutz/LetAppsAccessRadios**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt an, ob Windows apps zugreifen Sender steuern können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Benutzer im Steuerelement.
-   1 – Force ermöglichen.
-   2 - Force verweigern.

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 2.

<a href="" id="privacy-letappsaccessradios-forceallowtheseapps"></a>**Datenschutz/LetAppsAccessRadios\_ForceAllowTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführten apps haben Zugriff auf Sender steuern. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessRadios für die angegebene apps.

<a href="" id="privacy-letappsaccessradios-forcedenytheseapps"></a>**Datenschutz/LetAppsAccessRadios\_ForceDenyTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführte apps haben keinen Zugriff auf Sender steuern. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessRadios für die angegebene apps.

<a href="" id="privacy-letappsaccessradios-userincontroloftheseapps"></a>**Datenschutz/LetAppsAccessRadios\_UserInControlOfTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Der Benutzer kann die Sender für den Datenschutz für die aufgeführten apps zu steuern. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessRadios für die angegebene apps.

<a href="" id="privacy-letappsaccesstrusteddevices"></a>**Datenschutz/LetAppsAccessTrustedDevices**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt an, ob Windows apps vertrauenswürdige Geräte zugreifen können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Benutzer im Steuerelement.
-   1 – Force ermöglichen.
-   2 - Force verweigern.

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 2.

<a href="" id="privacy-letappsaccesstrusteddevices-forceallowtheseapps"></a>**Datenschutz/LetAppsAccessTrustedDevices\_ForceAllowTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführten apps haben Zugriff auf vertrauenswürdige Geräte. Diese Einstellung überschreibt die standardmäßige LetAppsAccessTrustedDevices richtlinieneinstellung für die angegebene apps.

<a href="" id="privacy-letappsaccesstrusteddevices-forcedenytheseapps"></a>**Datenschutz/LetAppsAccessTrustedDevices\_ForceDenyTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführten apps haben keinen Zugriff auf vertrauenswürdige Geräte. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessTrustedDevices für die angegebene apps.

<a href="" id="privacy-letappsaccesstrusteddevices-userincontroloftheseapps"></a>**Datenschutz/LetAppsAccessTrustedDevices\_UserInControlOfTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Der Benutzer kann die "Vertrauenswürdige Geräte" für den Datenschutz für die aufgeführten apps zu steuern. Diese Einstellung überschreibt die Einstellung Standard LetAppsAccessTrustedDevices für die angegebene apps.

<a href="" id="privacy-letappssyncwithdevices"></a>**Datenschutz/LetAppsSyncWithDevices**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt an, ob Windows-apps mit Geräten synchronisieren können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Benutzer im Steuerelement.
-   1 – Force ermöglichen.
-   2 - Force verweigern.

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 2.

<a href="" id="privacy-letappssyncwithdevices-forceallowtheseapps"></a>**Datenschutz/LetAppsSyncWithDevices\_ForceAllowTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführten apps haben Zugriff auf mit Geräten synchronisieren. Diese Einstellung überschreibt die standardmäßige LetAppsSyncWithDevices richtlinieneinstellung für die angegebene apps.

<a href="" id="privacy-letappssyncwithdevices-forcedenytheseapps"></a>**Datenschutz/LetAppsSyncWithDevices\_ForceDenyTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Aufgeführten apps haben keinen Zugriff mit Geräten synchronisieren. Diese Einstellung überschreibt die standardmäßige LetAppsSyncWithDevices richtlinieneinstellung für die angegebene apps.

<a href="" id="privacy-letappssyncwithdevices-userincontroloftheseapps"></a>**Datenschutz/LetAppsSyncWithDevices\_UserInControlOfTheseApps**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Liste der durch Semikolons getrennt Paket Kategorienamen von Windows Store-Apps. Der Benutzer kann die 'mit Geräten synchronisieren' für den Datenschutz für aufgeführte apps zu steuern. Diese Einstellung überschreibt die standardmäßige LetAppsSyncWithDevices richtlinieneinstellung für die angegebene apps.

<a href="" id="search-allowindexingencryptedstoresoritems"></a>**Suchen/AllowIndexingEncryptedStoresOrItems**  
<p style="margin-left: 20px">Zugelassen oder verweigert die Indizierung von Elementen. Diese Option ist für Windows Search Indexer die steuert, ob es Elemente indizieren wird, die wie die Windows-Schutz (WIP) geschützten Dateien verschlüsselt werden.

<p style="margin-left: 20px">Wenn die Richtlinie aktiviert ist, wird WIP geschützte Elemente indiziert sind, und die Metadaten zu diesen in einen unverschlüsselten Speicherort gespeichert werden. Die Metadaten enthält Elemente wie Dateipfad und Datum geändert.

<p style="margin-left: 20px">Wenn die Richtlinie deaktiviert ist, wird die WIP geschützte Elemente werden nicht indiziert und werden nicht in den Ergebnissen in Cortana oder Datei-Explorer angezeigt. Auch möglicherweise Leistungseinbußen auf Fotos und Groove-apps, wenn eine von WIP Vielzahl geschützte Dateien auf dem Gerät.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="search-allowsearchtouselocation"></a>**Suchen/AllowSearchToUseLocation**  
<p style="margin-left: 20px">Gibt an, ob die Suche Standortinformationen nutzen kann.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="search-allowusingdiacritics"></a>**Suchen/AllowUsingDiacritics**  
<p style="margin-left: 20px">Ermöglicht die Verwendung diakritischer Zeichen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="search-alwaysuseautolangdetection"></a>**Suchen/AlwaysUseAutoLangDetection**  
<p style="margin-left: 20px">Gibt an, ob die automatische Spracherkennung immer verwenden, bei der Indizierung von Inhalten und Eigenschaften.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="search-disablebackoff"></a>**Suchen/DisableBackoff**  
<p style="margin-left: 20px">Falls aktiviert, wird das Search Indexer Backoff Feature deaktiviert. Indizierung weiterhin mit voller Geschwindigkeit, auch wenn Systemaktivitäten hoch ist. Wenn deaktiviert, wird Backoff Logik Indizierung Aktivität wieder gedrosselt, wenn Systemaktivitäten hoch ist verwendet werden. Standardmäßig ist deaktiviert.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – deaktivieren.
-   1 – Enable.

<a href="" id="search-disableremovabledriveindexing"></a>**Suchen/DisableRemovableDriveIndexing**  
<p style="margin-left: 20px">Diese Einstellung konfiguriert, ob Bibliotheken Speicherorte auf Wechseldatenträgern hinzugefügt werden können.

<p style="margin-left: 20px">Wenn Sie diese Einstellung aktivieren, können nicht auf Wechseldatenträgern Speicherorte Bibliotheken hinzugefügt werden. Darüber hinaus können nicht auf Wechseldatenträgern Speicherorte indiziert werden.

<p style="margin-left: 20px">Wenn Sie deaktivieren oder diese Einstellung nicht konfigurieren, können Speicherorte auf Wechseldatenträgern Bibliotheken hinzugefügt werden. Darüber hinaus können Speicherorte auf Wechseldatenträgern indiziert werden.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – deaktivieren.
-   1 – Enable.

<a href="" id="search-preventindexinglowdiskspacemb"></a>**Suchen/PreventIndexingLowDiskSpaceMB**  
<p style="margin-left: 20px">Durch Aktivieren dieser Einstellung wird verhindert, dass Indizierung nicht nach weniger als die angegebene Menge an Speicherplatz auf demselben Laufwerk wie die Indexposition gelassen wird fortgesetzt werden kann. Wählen Sie zwischen 0 und 2.147.483.647 MB.

<p style="margin-left: 20px">Aktivieren Sie diese Richtlinie Computer in Ihrer Umgebung sehr Festplattenspeicher zur Verfügung steht.

<p style="margin-left: 20px">Wenn diese Richtlinie deaktiviert oder nicht konfiguriert ist, verwaltet die Windows-Desktopsuche automatisch die Indexgröße.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – deaktiviert.
-   1 (Standard) – aktivieren.

<a href="" id="search-preventremotequeries"></a>**Suchen/PreventRemoteQueries**  
<p style="margin-left: 20px">Wenn aktiviert, werden Clients konnte nicht dieses Computers Index remote abgefragt werden. Daher, wenn sie Netzwerkfreigaben durchsuchen, die auf diesem Computer gespeichert sind, werden sie nicht mit dem Index gesucht. Clientanforderungen für die Suche verwenden dieses Computers Index, wenn deaktiviert.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – deaktiviert.
-   1 (Standard) – aktivieren.

<a href="" id="search-safesearchpermissions"></a>**Suchen/SafeSearchPermissions**  
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Mobile erzwungen und im Windows-10 für Desktop nicht unterstützt.


<p style="margin-left: 20px">Gibt an, welche sicheres Suchen (Filterung Versender nicht jugendfreier Inhalte) erforderlich ist.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Strict, höchsten Filtern anhand Versender nicht jugendfreier Inhalte.
-   1 (Standard) – mäßig Filtern anhand der Versender nicht jugendfreier Inhalte (gültige Suchergebnisse werden nicht gefiltert).

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="security-allowaddprovisioningpackage"></a>**Security/AllowAddProvisioningPackage**  
<p style="margin-left: 20px">Gibt an, ob den Common Language Runtime-Konfigurations-Agent provisioning Packages installieren.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="security-allowautomaticdeviceencryptionforazureadjoineddevices"></a>**Security/AllowAutomaticDeviceEncryptionForAzureADJoinedDevices**  
> **Hinweis**  Diese Richtlinie ist in Windows-10, Version 1607 veraltet

<br>

> **Hinweis**  Diese Richtlinie ist nur für Desktop in Windows 10 erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">Gibt an, ob automatische geräteverschlüsselung während OOBE zulassen, wenn das Gerät Azure AD ist zugeordnet.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="security-allowmanualrootcertificateinstallation"></a>**Security/AllowManualRootCertificateInstallation**  
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Mobile erzwungen und im Windows-10 für Desktop nicht unterstützt.


<p style="margin-left: 20px">Gibt an, ob der Benutzer manuell installieren Stamm und Zertifikate.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="security-allowremoveprovisioningpackage"></a>**Security/AllowRemoveProvisioningPackage**  
<p style="margin-left: 20px">Gibt an, ob den Common Language Runtime-Konfigurations-Agent um provisioning Pakete zu entfernen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="security-antitheftmode"></a>**Security/AntiTheftMode**  
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Mobile erzwungen und im Windows-10 für Desktop nicht unterstützt.

 
<p style="margin-left: 20px">Ermöglicht oder disallow Anti-Diebstahl-Modus auf dem Gerät.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – zulassen keine Anti Diebstahl Modus.
-   1 (Standard) – Anti-Diebstahl-Modus wird die Standardkonfiguration für Gerät (Region abhängig) folgen.

<a href="" id="security-preventautomaticdeviceencryptionforazureadjoineddevices"></a>**Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices**  
> **Hinweis**  Diese Richtlinie ist nur für Desktop in Windows 10 erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">In Windows-10, Version 1607 ersetzen die veraltete Richtlinie **Security/AllowAutomaticDeviceEncryptionForAzureADJoinedDevices**hinzugefügt.

<p style="margin-left: 20px">Gibt an, ob automatische geräteverschlüsselung während OOBE zulassen, wenn das Gerät Azure AD ist zugeordnet.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – Verschlüsselung aktiviert ist.
-   1 – Verschlüsselung deaktiviert.

<a href="" id="security-requiredeviceencryption"></a>**Security/RequireDeviceEncryption**  
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Mobile erzwungen. In Windows-10 für Desktop können Sie den Status der Verschlüsselung Abfragen, mithilfe des Knotens [DeviceStatus CSP](devicestatus-csp.md) **DeviceStatus/Compliance/EncryptionCompliance**.


<p style="margin-left: 20px">Ermöglicht es Unternehmen, Zentralspeicher-Verschlüsselung zu aktivieren.

> **Wichtig**  BitLocker muss vor der Verwendung dieser Richtlinie auf dem Gerät aktiviert sein.


<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – die Verschlüsselung ist nicht erforderlich.
-   1 – Verschlüsselung ist erforderlich.

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 1.

> **Wichtig**  Wenn Verschlüsselung aktiviert wurde, kann es deaktiviert werden diese Richtlinie verwenden.


<a href="" id="security-requireprovisioningpackagesignature"></a>**Security/RequireProvisioningPackageSignature**  
<p style="margin-left: 20px">Gibt an, ob provisioning Pakete ein Zertifikat von einer Gerät vertrauenswürdige Zertifizierungsstelle signiert sein muss.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – nicht erforderlich sind.
-   1 – erforderlich.

<a href="" id="security-requireretrievehealthcertificateonboot"></a>**Security/RequireRetrieveHealthCertificateOnBoot**  
<p style="margin-left: 20px">Gibt an, ob abrufen und buchen TCG Boot-Protokolle und abzurufen oder eine verschlüsselte oder signierte Bescheinigung Integritätsberichte für aus Microsoft Health Bescheinigung Service (HAS) zwischenspeichern, wenn ein Gerät gestartet oder neu gestartet wird.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – nicht erforderlich sind.
-   1 – erforderlich.

<p style="margin-left: 20px">Wenn diese Richtlinie auf 1 (erforderlich):

-   Bestimmt, ob ein Gerät kann Remote Gerät Bescheinigung, durch Überprüfen, ob das Gerät TPM 2.0 hat.
-   Verbessert die Leistung des Geräts werden, da das Gerät zum Abrufen und Zwischenspeichern von Daten, um die Wartezeit bei der Überprüfung der Integrität Gerät zu reduzieren.

> **Hinweis**  Es wird empfohlen, dass diese Richtlinie erforderlichen nach der Registrierung MDM festgelegt ist.
 

<p style="margin-left: 20px">Die meisten eingeschränktem Wert ist 1.

<a href="" id="settings-allowautoplay"></a>**Einstellungen/AllowAutoPlay**   
> **Hinweis**  Diese Richtlinie ist nur für Desktop in Windows 10 erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">Den Benutzer Auto Play Einstellungen ändern können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

> **Hinweis**  Wenn diese Richtlinie auf 0 (nicht zulässig) wirkt sich nicht auf das Dialogfeld Automatische Wiedergabe aus, die angezeigt wird, wenn ein Gerät angeschlossen ist.


<a href="" id="settings-allowdatasense"></a>**Einstellungen/AllowDataSense**  
<p style="margin-left: 20px">Ermöglicht es dem Benutzer Daten Sinne Einstellungen ändern.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="settings-allowdatetime"></a>**Einstellungen/AllowDateTime**  
<p style="margin-left: 20px">Ermöglicht es dem Benutzer zu ändern, Datum und die Uhrzeit aus.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="settings-alloweditdevicename"></a>**Einstellungen/AllowEditDeviceName**  
<p style="margin-left: 20px">Ermöglicht das Bearbeiten des Gerätenamens.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="settings-allowlanguage"></a>**Einstellungen/AllowLanguage**  
> **Hinweis**  Diese Richtlinie ist nur für Desktop in Windows 10 erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">Ermöglicht dem Benutzer die spracheinstellungen ändern.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="settings-allowpowersleep"></a>**Einstellungen/AllowPowerSleep**  
> **Hinweis**  Diese Richtlinie ist nur für Desktop in Windows 10 erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">Ermöglicht es dem Benutzer zu ändern, Power Energiesparmodus Einstellungen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="settings-allowregion"></a>**Einstellungen/AllowRegion**  
> **Hinweis**  Diese Richtlinie ist nur für Desktop in Windows 10 erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">Ermöglicht dem Benutzer die regionseinstellungen ändern.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="settings-allowsigninoptions"></a>**Einstellungen/AllowSignInOptions**  
> **Hinweis**  Diese Richtlinie ist nur für Desktop in Windows 10 erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">Ermöglicht es dem Benutzer Anmeldeoptionen ändern.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="settings-allowvpn"></a>**Einstellungen/AllowVPN**  
<p style="margin-left: 20px">Ermöglicht es dem Benutzer VPN-Einstellungen ändern.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="settings-allowworkplace"></a>**Einstellungen/AllowWorkplace**  
> **Hinweis**  Diese Richtlinie ist nur für Desktop in Windows 10 erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">Ermöglicht Benutzer das Jahrestag Einstellungen ändern.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="settings-allowyouraccount"></a>**Einstellungen/AllowYourAccount**  
<p style="margin-left: 20px">Ermöglicht Benutzer das Konto zu ändern.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="speech-allowspeechmodelupdate"></a>**Spracherkennung/AllowSpeechModelUpdate**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt an, ob das Gerät Updates für die Spracherkennung und die Spracherkennung-Synthese Modelle entgegennimmt. Ein Speech-Objektmodell enthält Daten vom Sprachmodul zur Audio in Text (oder umgekehrt) zu konvertieren. Die Modelle werden regelmäßig aktualisiert, um die Genauigkeit und Leistung zu verbessern. Modelle sind nicht ausführbaren Datendateien. Falls aktiviert, das Gerät aktualisierte Speech-Modelle in regelmäßigen Abständen überprüft und Laden Sie sie aus einem Microsoft-Dienst mithilfe der Hintergrund Internet Hintergrundübertragungsdienst (BITS).

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="start-forcestartsize"></a>**Start/ForceStartSize**  
> **Hinweis**  Diese Richtlinie ist nur für Desktop in Windows 10 erzwungen und in Windows 10 Mobile nicht unterstützt.


<p style="margin-left: 20px">Erzwingt die Bildschirmgröße starten.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – erzwingen Größe der Start nicht.
-   1 – nicht Fullscreen Größe der Start zu erzwingen.
-   2 - Force ein Fullscreen-Größe der Start.

<p style="margin-left: 20px">Wenn Richtlinie Konfigurationskonflikt vorliegt, wird die aktuelle Konfiguration-Anforderung an das Gerät angewendet.

<a href="" id="start-startlayout"></a>**Start/StartLayout**   
> **Wichtige**  Dieser Knoten ist für jeden Benutzer einzeln festgelegt und müssen die folgenden Pfade mit zugegriffen werden: > -   **./User/Vendor/MSFT/Policy/Config/Start/StartLayout** , um die Richtlinie zu konfigurieren.
> -   **./User/Vendor/MSFT/Policy/Result/Start/StartLayout** zum Abfragen des aktuellen Werts der Richtlinie.


<p style="margin-left: 20px">Ermöglicht Ihnen das Standardlayout Start überschreiben und verhindert, dass den Benutzer geändert wird.

<p style="margin-left: 20px">Diese Richtlinie wird in [Start/StartLayout Beispielen](#startlayout-examples) weiter unten in diesem Thema beschrieben werden.

<a href="" id="system-allowbuildpreview"></a>**System/AllowBuildPreview**   
> **Hinweis**  Diese Einstellung gilt nur für Geräte, auf denen Windows 10 Pro, Windows 10 Enterprise und Windows 10 Education, Windows 10 Mobile und Windows 10 Mobile Enterprise.


<p style="margin-left: 20px">Diese Einstellung bestimmt, ob Benutzer die Insider Build Steuerelemente im erweiterte Optionen für Windows Update zugreifen können. Diese Steuerelemente befinden sich unter "Get-Insider Builds" und Aktivieren von Benutzern auf ihren Geräten herunterladen und Installieren von Windows Preview-Software zur Verfügung stellen.

<p style="margin-left: 20px">Wenn Sie aktivieren oder diese Einstellung nicht konfigurieren, können Benutzer herunterladen und installieren Windows Preview-Software auf ihren Geräten. Wenn Sie diese Einstellung deaktivieren, wird das Element "Get-Insider Builds" nicht verfügbar.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen. Das Element "Get-Insider Builds" ist nicht verfügbar, die Benutzer können sich nicht um ihre Geräte für die Preview-Software verfügbar zu machen.
-   1 – zulässig. Benutzer können ihren Geräten zum Herunterladen und Installieren der Preview-Software zur Verfügung stellen.
-   2 (Standard) – nicht konfiguriert. Benutzer können ihren Geräten zum Herunterladen und Installieren der Preview-Software zur Verfügung stellen.

<a href="" id="system-allowembeddedmode"></a>**System/AllowEmbeddedMode**  
<p style="margin-left: 20px">Gibt an, ob die allgemeine Gerät im eingebetteten Modus werden festgelegt.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – nicht zugelassen.
-   1 – zulässig.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="system-allowexperimentation"></a>**System/AllowExperimentation**   
> **Hinweis** Diese Richtlinie wird in der Windows-10, Version 1607 nicht unterstützt.

<p style="margin-left: 20px">Diese Einstellung bestimmt die Ebene, die mit dem Produkt Studie Benutzervoreinstellungen oder Gerät Verhalten Microsoft experimentieren kann.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – deaktiviert.
-   1 (Standard) – ermöglicht Microsoft so konfigurieren Sie nur für Geräte.
-   2 – können Microsoft vollständige Experimentations durchführen.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="system-allowlocation"></a>**System/AllowLocation**  
<p style="margin-left: 20px">Gibt an, ob das app-Zugriff auf den Dienst Speicherort zugelassen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Force Speicherort deaktiviert. Alle Einstellungen für Datenschutz für den Standort gelten umgeschaltet deaktiviert und abgeblendet. Benutzer können die Einstellungen nicht ändern, und keine apps dürfen Zugriff auf den Speicherort-Dienst, einschließlich Cortana, und suchen.
-   1 (Standard) – ist ortungsdienstes zulässig ist. Der Benutzer hat die Kontrolle und Datenschutz für den Standort-Einstellungen ändern, aktiviert oder deaktiviert.
-   2 – erzwingen Sie Speicherort auf. Alle Einstellungen für Datenschutz für den Standort gelten auf umgeschaltet und abgeblendet. Benutzer können die Einstellungen nicht ändern, und alle seine Zustimmung Berechtigungen werden automatisch unterdrückt.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<p style="margin-left: 20px">Während die Richtlinie auf 0 (Force Speicherort Off) oder 2 (Force Speicherort auf) festgelegt ist, würde eine beliebige Serviceeinsatz Speicherort aus einer app durch diese Richtlinie festgelegten Wert ausgelöst.

<p style="margin-left: 20px">Wenn die Richtlinie von 0 (Force Speicherort Off) oder 2 (Force Speicherort auf) und 1 (Benutzersteuerelement) zu wechseln, wird die app auf die ursprünglichen Speicherort Service zurückgesetzt.

<p style="margin-left: 20px">Beispielsweise ist eine app ursprünglichen Speicherort Einstellung deaktiviert. Der Administrator legt die Richtlinie **AllowLocation** klicken Sie dann auf 2 (Force Speicherort auf.) Dem Starten des Diensts Speicherort für diese app, die ursprüngliche Einstellung überschreiben arbeiten. Wenn der Administrator die Richtlinie **AllowLocation** zurück zur 1 (Benutzersteuerelement) wechselt, wird später die app zurückgesetzt, verwenden Sie die ursprüngliche Einstellung des deaktiviert.

<a href="" id="system-allowstoragecard"></a>**System/AllowStorageCard**  
<p style="margin-left: 20px">Steuert, ob der Benutzer berechtigt ist, verwenden Sie die Speicherkarte für Speicher des Geräts. Diese Einstellung wird verhindert, dass programmgesteuerten Zugriff auf die Speicherkarte.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – SD-Karte Verwendung ist nicht zulässig, und USB-Laufwerke sind deaktiviert. Diese Einstellung verhindert nicht den programmgesteuerten Zugriff auf die Speicherkarte. 
-   1 (Standard) – zulassen eine Speicherkarte.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="system-allowtelemetry"></a>**System/AllowTelemetry**  
<p style="margin-left: 20px">Zulassen Sie diesem Gerät zum Senden von Diagnose- und Verwendungsanalyse Telemetriedaten, beispielsweise Watson.

<p style="margin-left: 20px">Die folgenden Tabellen beschreiben die unterstützten Werte:

<table style="margin-left: 20px">
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th>Windows 8.1 Werte</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>0 – nicht zugelassen.</p>
</td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p> 1 – zulässig, außer für sekundäre Anforderungen.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>2 (Standard) – zulässig.</p></td>
</tr>
</tbody>
</table>


<table style="margin-left: 20px">
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th>Windows-10-Werte</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>0 – Sicherheit. Informationen sind, die Windows sicherer, einschließlich der Daten über die Benutzeroberfläche verbunden und Telemetrie komponenteneinstellungen, böswilligen Tool zum Entfernen der Software und Windows Defender schützen erforderlich.</p>
<div class="alert">
<strong>Hinweis</strong>  Dieser Wert gilt nur für Windows 10 Enterprise, Windows 10 Education, Windows 10 Mobile Enterprise, Windows 10 IoT Core (IoT Core) und Windows Server 2016. Mit dieser Einstellung auf anderen Geräten entspricht dem Festlegen des Werts von 1.
</div>
</td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>1 – einfach. Grundlegende Device Info, einschließlich: Daten im Zusammenhang mit Qualität, app-Kompatibilität, app-Verwendungsdaten und Daten aus der Sicherheitsstufe.</p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>2 – erweitert. Zusätzliche Hinweise, einschließlich: wie Windows, Windows Server, System Center und apps verwendet werden, die Leistung, erweiterte Zuverlässigkeit Daten und Daten aus der Basic und die Sicherheitsstufen.</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>3 – vollständige. Alle Daten erforderlich sind, um identifizieren und Ihnen dabei helfen, um Probleme zu beheben, einschließlich Daten aus der Sicherheit, Basic und erweiterte anzeigen.</p></td>
</tr>
</tbody>
</table>


> **Wichtig**  Wenn Sie Windows 8.1 MDM Server verwenden und der Wert der Richtlinie der Vorversion AllowTelemetry auf einem Windows-10-Mobile-Gerät mit 0 festgelegt, der Wert wird nicht berücksichtigt, und die Telemetrie-Ebene im Hintergrund auf der Ebene 1 festgelegt ist.


<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="system-allowusertoresetphone"></a>**System/AllowUserToResetPhone**   
> **Hinweis**  Diese Richtlinie ist nur in Windows 10 Mobile erzwungen und im Windows-10 für Desktop nicht unterstützt.


<p style="margin-left: 20px">Gibt an, ob der Benutzer Factory des Telefons mit Control Panel und Hardware Tastenkombination zurücksetzen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zum Zurücksetzen auf Standardeinstellungen Factory zulässig.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="system-telemetryproxy"></a>**System/TelemetryProxy**  
<p style="margin-left: 20px">Können Sie den vollqualifizierten Domänennamen (FQDN) oder IP-Adresse eines Proxyservers Benutzererlebnis verbunden und Telemetrie Anforderungen weiterleiten an. Das Format für diese Einstellung ist * &lt;Server&gt;:&lt;Port&gt;*. Die Verbindung wird hergestellt über eine Verbindung (Secure Sockets Layer, SSL). Ausfall der benannte Proxy oder vorhanden ist, dass kein Proxy angegeben werden, wenn diese Richtlinie aktiviert ist, wird die Benutzererlebnis verbunden und Telemetrie Daten nicht übertragen werden und bleibt auf dem lokalen Gerät.

<p style="margin-left: 20px">Wenn Sie deaktivieren oder diese Einstellung nicht konfigurieren, Benutzererlebnis verbunden und Telemetriedaten an Microsoft gelangen mithilfe der Standardkonfiguration für den Proxy.

<a href="" id="textinput-allowimelogging"></a>**TextInput/AllowIMELogging**   
> **Hinweis**  Die Richtlinie wird nur für Desktop in Windows 10 erzwungen.


<p style="margin-left: 20px">Ermöglicht es dem Benutzer zu aktivieren und Deaktivieren der Protokollierung für die Konvertierung von falschen und speichern automatische Abstimmung Ergebnis in eine Datei und vorhersehbare Eingabe Verlauf-basierte aus.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="textinput-allowimenetworkaccess"></a>**TextInput/AllowIMENetworkAccess**   
> **Hinweis**  Die Richtlinie wird nur für Desktop in Windows 10 erzwungen.


<p style="margin-left: 20px">Ermöglicht es dem Benutzer aktivieren offenes erweitertes Wörterbuch, Internet Integration der Suchfunktion oder Cloud Candidate Features input Vorschläge bereitstellen, die nicht in das Gerät lokalen Wörterbuch vorhanden sind.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="textinput-allowinputpanel"></a>**TextInput/AllowInputPanel**   
> **Hinweis**  Die Richtlinie wird nur für Desktop in Windows 10 erzwungen.


<p style="margin-left: 20px">Ermöglicht der IT-Administrator die Fingereingabe/Handschrift Tastatur unter Windows zu deaktivieren.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="textinput-allowjapaneseimesurrogatepaircharacters"></a>**TextInput/AllowJapaneseIMESurrogatePairCharacters**   
> **Hinweis**  Die Richtlinie wird nur für Desktop in Windows 10 erzwungen.


<p style="margin-left: 20px">Ermöglicht den IME für Japanisch Ersatz Paar Zeichen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="textinput-allowjapaneseivscharacters"></a>**TextInput/AllowJapaneseIVSCharacters**   
> **Hinweis**  Die Richtlinie wird nur für Desktop in Windows 10 erzwungen.


<p style="margin-left: 20px">Japanische Ideographisches Variation Sequenz (IVS) Zeichen ermöglicht.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="textinput-allowjapanesenonpublishingstandardglyph"></a>**TextInput/AllowJapaneseNonPublishingStandardGlyph**   
> **Hinweis**  Die Richtlinie wird nur für Desktop in Windows 10 erzwungen.


<p style="margin-left: 20px">Ermöglicht das japanische Standardsymbol nicht veröffentlichen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="textinput-allowjapaneseuserdictionary"></a>**TextInput/AllowJapaneseUserDictionary**   
> **Hinweis**  Die Richtlinie wird nur für Desktop in Windows 10 erzwungen.


<p style="margin-left: 20px">Ermöglicht das japanische Benutzerwörterbuch.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="textinput-allowkoreanextendedhanja"></a>**TextInput/AllowKoreanExtendedHanja**  
<p style="margin-left: 20px">Diese Richtlinie ist veraltet.

<a href="" id="textinput-allowlanguagefeaturesuninstall"></a>**TextInput/AllowLanguageFeaturesUninstall**   
> **Hinweis**  Die Richtlinie wird nur für Desktop in Windows 10 erzwungen.


<p style="margin-left: 20px">Ermöglicht die Deinstallation von Sprachfeatures wie Rechtschreibprüfung Dame, auf einem Gerät.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="textinput-allowlinguisticdatacollection"></a>**TextInput/AllowLinguisticDataCollection**  
<p style="margin-left: 20px">Ermöglicht das Senden an Microsoft Benutzer Text eingegebenen Daten, die für Verbesserungen bei zukünftigen Model Samples (anonymisiert) gesammelt werden.

> **Wichtig**  Texteingabe eingegeben mithilfe bestimmter Eingabebereich Felder wie e-Mail-Adresse, Anmeldenamen, Kennwörter und Telefonnummern aus alle Stichproben ausgeschlossen werden.


<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<a href="" id="textinput-excludejapaneseimeexceptjis0208"></a>**TextInput/ExcludeJapaneseIMEExceptJIS0208**  
> **Hinweis**  Die Richtlinie wird nur für Desktop in Windows 10 erzwungen.


<p style="margin-left: 20px">Ermöglicht den Benutzern Code Zeichenbereich Umrechnung einschränken, indem Sie den Zeichen Filter festlegen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – keine Zeichen gefiltert werden.
-   1 – alle Zeichen mit Ausnahme von JIS0208 werden gefiltert.

<a href="" id="textinput-excludejapaneseimeexceptjis0208andeudc"></a>**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**  
> **Hinweis**  Die Richtlinie wird nur für Desktop in Windows 10 erzwungen.


<p style="margin-left: 20px">Ermöglicht den Benutzern Code Zeichenbereich Umrechnung einschränken, indem Sie den Zeichen Filter festlegen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – keine Zeichen gefiltert werden.
-   1 – alle Zeichen mit Ausnahme von JIS0208 und EUDC gefiltert werden.

<a href="" id="textinput-excludejapaneseimeexceptshiftjis"></a>**TextInput/ExcludeJapaneseIMEExceptShiftJIS**  
> **Hinweis**  Die Richtlinie wird nur für Desktop in Windows 10 erzwungen.


<p style="margin-left: 20px">Ermöglicht den Benutzern Code Zeichenbereich Umrechnung einschränken, indem Sie den Zeichen Filter festlegen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – keine Zeichen gefiltert werden.
-   1 – alle Zeichen mit Ausnahme von ShiftJIS gefiltert werden.

<a href="" id="update-activehoursend"></a>**Update/ActiveHoursEnd**  
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise


<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Ermöglicht der IT-Administrator (bei Verwendung mit **Update/ActiveHoursStart**) zum Verwalten von eines Bereichs des aktiven Stunden, in dem Update Neustarts nicht geplant werden. Dieser Wert wird die Endzeit. Es gibt 12-Stunden maximale aus Startzeit.

<p style="margin-left: 20px">Unterstützte Werte sind 0 – 23, 0 ist, auf dem 00: 00 Uhr, 1 ist 1 h, Etc.

<p style="margin-left: 20px">Der Standardwert ist 17 (17: 00 Uhr).

<a href="" id="update-activehoursstart"></a>**Update/ActiveHoursStart**   
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise


<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Ermöglicht die IT-Administrator (bei Verwendung mit **Update/ActiveHoursEnd**) zum Verwalten von eines Bereichs von Stunden wobei Update Neustarts nicht geplant werden. Dieser Wert wird die Startzeit. Es gibt 12-Stunden maximale aus Startzeit.

<p style="margin-left: 20px">Unterstützte Werte sind 0 – 23, 0 ist, auf dem 00: 00 Uhr, 1 ist 1 h, Etc.

<p style="margin-left: 20px">Der Standardwert ist 8 (8: 00).

<a href="" id="update-allowautoupdate"></a>**Update/AllowAutoUpdate**   
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise


<p style="margin-left: 20px">Ermöglicht der IT-Administrator zum Verwalten von Automatische Updateverhalten, um zu überprüfen, herunterladen und Installieren von Updates.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Get und ersetzen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – benachrichtigen den Benutzer vor dem Update herunterladen. Diese Richtlinie wird vom Unternehmen verwendet, die die Endbenutzern zum Verwalten von datennutzungs-aktivieren möchte. Mit dieser Option werden Benutzer benachrichtigt, wenn Updates, die gelten für das Gerät und zum Download bereit. Benutzer können herunterladen und Installieren von Updates von der Windows Update-Systemsteuerung.
-   1 – automatische Update installieren und benachrichtigt dann den Benutzer so planen Sie einen Neustart des Geräts. Updates in Netzwerken nicht gemessene automatisch heruntergeladen und installiert während "Automatische Verwaltung", wenn das Gerät nicht verwendet wird und nicht auf Batterie ausgeführt wird. Automatische Wartung kann nicht zum Installieren von Updates für zwei Tage ist, wird Windows Update Updates sofort installieren. Wenn die Installation ein Neustart erforderlich ist, wird der Endbenutzer aufgefordert, um den Zeitplan neu starten. Der Endbenutzer hat bis zu sieben Tage so planen Sie die neu starten und anschließend ein Neustart des Geräts erzwungen wird. Aktivieren der Endbenutzers die Startzeit steuern verringert das Risiko von versehentlichen Datenverlust aufgrund von Anwendungen, die beim Herunterfahren nicht ordnungsgemäß beim Neustart des Computers nicht ausführen.
-   2 (Standard) – automatische Installieren und neu starten. Updates in Netzwerken nicht gemessen automatisch heruntergeladen und installiert während "Automatische Verwaltung", wenn das Gerät nicht verwendet wird und nicht auf Batterie ausgeführt wird. Wenn die automatische Wartung kann nicht zum Installieren von Updates für zwei Tage ist, wird Windows Update sofort Updates installieren. Wenn ein Neustart erforderlich ist, klicken Sie dann das Gerät automatisch neu gestartet wird, wenn das Gerät nicht aktiv verwendet wird. Dies ist das Standardverhalten für nicht verwaltete Geräte. Geräte schnell aktualisiert werden, aber es erhöhen das Risiko eines unbeabsichtigten Datenverluste durch eine Anwendung, die nicht herunterfahren ordnungsgemäß beim Neustart lässt.
-   3 – automatische Installieren und zu einem bestimmten Zeitpunkt starten. Die IT gibt Installation Datum und Uhrzeit an. Wenn kein Tag und die Uhrzeit angegeben sind, ist die Standardeinstellung täglich 03: 00 Uhr. Automatische Installation erfolgt zu diesem Zeitpunkt und Neustart des Geräts geschieht nach einen Countdown 15 Minuten. Wenn der Benutzer angemeldet ist, wenn Windows Neustart bereit ist, kann der Benutzer den Countdown 15 Minuten, um den Neustart zu verzögern unterbrochen werden.
-   4 – automatische Installieren und neu starten, ohne Kontrolle durch den Endbenutzer. Updates in Netzwerken nicht gemessene automatisch heruntergeladen und installiert während "Automatische Verwaltung", wenn das Gerät nicht verwendet wird und nicht auf Batterie ausgeführt wird. Wenn die automatische Wartung kann nicht zum Installieren von Updates für zwei Tage ist, wird Windows Update sofort Updates installieren. Wenn ein Neustart erforderlich ist, klicken Sie dann das Gerät automatisch neu gestartet wird, wenn das Gerät nicht aktiv verwendet wird. Diese Einstellung Option wird auch die Endbenutzer-Systemsteuerung auf schreibgeschützt.
-   5 – automatische Updates deaktivieren.

    > **Wichtig**  Diese Option sollte nur für Systeme unter Einhaltung von Vorschriften, verwendet werden, wie Sie Sicherheitsupdates auch nicht abgerufen werden.
 

<p style="margin-left: 20px">Wenn die Richtlinie nicht konfiguriert ist, rufen Sie Endbenutzern das Standardverhalten (automatische Installieren und neu starten).

<a href="" id="update-allowmuupdateservice"></a>**Update/AllowMUUpdateService**   
> **Hinweis**  Diese Richtlinie steht unter Windows 10 Pro, Windows 10 Enterprise und Windows 10 Bildungseinrichtungen


<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Ermöglicht der IT-Administrator zum Verwalten von fest, ob nach app-Updates von Microsoft Update.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen oder nicht konfiguriert.
-   1 – zulässig. Updates über Microsoft Update empfangen akzeptiert.

<a href="" id="update-allownonmicrosoftsignedupdate"></a>**Update/AllowNonMicrosoftSignedUpdate**  
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise


<p style="margin-left: 20px">Ermöglicht der IT-Administrator verwalten, ob automatische Updates akzeptiert Updates von Entitäten als Microsoft signiert werden, wenn das Update an der Position UpdateServiceUrl gefunden wird. Diese Richtlinie unterstützt die Verwendung von WSUS für die 3. Partei Software- und Patch-Verteilung.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Get und ersetzen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen oder nicht konfiguriert. Updates aus einem Intranet Microsoft Update Service Location müssen von Microsoft signiert sein.
-   1 – zulässig. Akzeptiert die Updates, die über ein Intranet Microsoft Update Service Location empfangen, wenn sie mit einem Zertifikat im Zertifikatspeicher des lokalen Computers "Vertrauenswürdige Herausgeber" gefunden signiert sind.

<p style="margin-left: 20px">Diese Richtlinie gilt für desktop und lokale Veröffentlichung über WSUS 3. Partei Updates (Binärdateien und Updates auf Microsoft Update nicht gehostet) und ermöglicht IT verwalten, ob automatische Updates akzeptiert Updates von Entitäten als Microsoft signiert werden, wenn das Update auf einem Intranet Microsoft Update Service Location gefunden wird.

<a href="" id="update-allowupdateservice"></a>**Update/AllowUpdateService**   
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro, Windows 10 Enterprise, Windows 10 Schulung und Windows 10 Mobile Enterprise


<p style="margin-left: 20px">Gibt an, ob das Gerät Microsoft Update, Windows Server Update Services (WSUS) oder Windows Store verwendet werden konnte.

<p style="margin-left: 20px">Selbst wenn Windows Update konfiguriert ist, Updates von einer internen Updatedienst erhalten, wird es in regelmäßigen Abständen Informationen aus der öffentlichen Windows Update-Dienst so aktivieren Sie künftig zum Aktualisieren von Windows und andere Dienste wie Microsoft Update oder Windows Store abzurufen

<p style="margin-left: 20px">Durch Aktivieren dieser Richtlinie wird diese Funktionalität deaktivieren und möglicherweise die Verbindung mit öffentlichen Diensten wie etwa Windows Store nicht mehr funktioniert.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – Update-Dienst nicht zulässig.
-   1 (Standard) – ist Updatedienst zulässig ist.

> **Hinweis**  Diese Richtlinie gilt nur bei der Desktop oder Gerät konfiguriert ist zum Herstellen eines Updatedienst mit der Richtlinie "Specify Intranet Microsoft Update Service Location".


<a href="" id="update-branchreadinesslevel"></a>**Update/BranchReadinessLevel**  
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise


<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Ermöglicht der IT-Administrator, welche zweigstellenbereitstellung ein Gerät empfängt ihre Updates von festgelegt.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   16 (Standard) – Ruft den Benutzer alle anwendbaren Upgrades von aktuellen Branch (CB).
-   32 – Benutzer ruft Upgrades aus Zweig aktuell für die Business (CBB) ab.

<a href="" id="update-deferfeatureupdatesperiodindays"></a>**Update/DeferFeatureUpdatesPeriodInDays**  
> **Hinweis**  Diese Richtlinie ist auf Windows 10 Pro, Windows 10 Enterprise, Windows 10 Education verfügbar.
<p style="margin-left: 20px">Da diese Richtlinie nicht gesperrt ist, erhalten Sie bei Verwendung einer Windows 10 Mobile-Gerät konfigurieren keine Fehlermeldung angezeigt. Die Richtlinie wird jedoch nicht wirksam wird.


<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Verzögert Feature Updates für die angegebene Anzahl von Tagen an.

<p style="margin-left: 20px">Unterstützte Werte sind 0 180.

<a href="" id="update-deferqualityupdatesperiodindays"></a>**Update/DeferQualityUpdatesPeriodInDays**   
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise


<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Verzögert Qualität Updates für die angegebene Anzahl von Tagen an.

<p style="margin-left: 20px">Unterstützte Werte sind 0 bis 30.

<a href="" id="update-deferupdateperiod"></a>**Update/DeferUpdatePeriod**   
> **Hinweis**  
> Diese Richtlinie steht auf Windows 10 Pro, Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise >> nicht verwenden diese Richtlinie in Windows 10, Version 1607 Geräte, stattdessen die neuen Richtlinien, die in [Windows-10, Version 1607 für aktualisieren Management](device-update-management.md#windows10version1607forupdatemanagement)aufgelistet. Sie können weiterhin DeferUpdatePeriod für Windows 10, Version 1511-Geräte verwenden.


<p style="margin-left: 20px">Ermöglicht es IT-Administratoren Update Verzögerungen für bis zu vier Wochen angeben.

<p style="margin-left: 20px">Unterstützte Werte sind 0-4 ist, bezieht sich auf die Anzahl der Wochen Updates zu verzögern.

<p style="margin-left: 20px">In Windows 10 Mobile Enterprise-Version 1511 Geräte legen Sie auf automatische Updates, für DeferUpdatePeriod arbeiten müssen Sie Folgendes festlegen:

-   Update/RequireDeferUpgrade muss auf 1 festgelegt werden
-   System/AllowTelemetry muss mindestens auf 1 festgelegt werden

<p style="margin-left: 20px">Wenn die Richtlinie "Specify Intranet Microsoft Update Service Location" aktiviert ist, haben Sie dann die "Defer Upgrades durch" sowie "Defer Aktualisierungen durch" und "Anhalten Updates und Upgrades" Einstellungen keine Auswirkung.

<p style="margin-left: 20px">Wenn die Richtlinie Telemetrie zulassen aktiviert ist und der Optionen-Wert auf 0 festgelegt ist, haben Sie dann die "Defer Upgrades durch" sowie "Defer Aktualisierungen durch" und "Anhalten Updates und Upgrades" Einstellungen keine Auswirkung.

<table style="margin-left: 20px">
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Aktualisieren der Kategorie</th>
<th>Maximale Verzögerungen</th>
<th>Rückstellung Schrittweite</th>
<th>Geben Sie/Update Hinweise</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top"><p>Betriebssystem aktualisieren</p></td>
<td style="vertical-align:top"><p>8 Monaten</p></td>
<td style="vertical-align:top"><p>1 Monat</p></td>
<td style="vertical-align:top"><p>Upgrade – 3689BDC8-B205-4AF4-8D4A-A63924C5E9D5</p></td>
</tr>
<tr class="even">
<td style="vertical-align:top"><p>Update</p></td>
<td style="vertical-align:top"><p>1 Monat</p></td>
<td style="vertical-align:top"><p>1 Woche</p></td>
<td style="vertical-align:top"><div class="alert">
<strong>Hinweis</strong>  Wenn ein Computer Microsoft Update aktiviert ist, alle Microsoft-Updates in den folgenden Kategorien auch Defer beobachten / Pause Logik.
</div>
<ul>
<li>Sicherheitsupdate - 0FA1201D-4330-4FA8-8AE9-B877473B6441</li>
<li>Wichtige Update - E6CF1350-C01B-414D-A61F-263D14D133B4</li>
<li>Updaterollup - 28BC880E-0592-4CBF-8F95-C79B17911D5F</li>
<li>Service Pack - 68C5B0A3-D1A6-4553-AE49-01D3A7827828</li>
<li>Tools - B4832BD8-E735-4761-8DAF-37F882276DAB</li>
<li>Feature Pack - B54E7D24-7ADD-428F-8B75-90A396FA584F</li>
<li>Update - CD5FFD1E-E932-4E3A-BF74-18BF0B1BBD83</li>
<li>Treiber - EBFC1FC5-71A4-4F7B-9ACA-3B9A503104A0</li>
</ul></td>
</tr>
<tr class="odd">
<td style="vertical-align:top"><p>Andere / verzögern kann nicht</p></td>
<td style="vertical-align:top"><p>Keine Rückstellung</p></td>
<td style="vertical-align:top"><p>Keine Rückstellung</p></td>
<td style="vertical-align:top"><p>Jede Update-Kategorie, die nicht explizit über fällt in dieser Kategorie aufgelistet.</p>
<p>Definition Update - E0789628-CE08-4437-BE74-2495B842F43B</p></td>
</tr>
</tbody>
</table>


<a href="" id="update-deferupgradeperiod"></a>**Update/DeferUpgradePeriod**   
> **Hinweis**  
> Diese Richtlinie ist auf Windows 10 Pro, Windows 10 Enterprise, Windows 10 Educatio verfügbarn.

> Da diese Richtlinie nicht gesperrt ist, erhalten Sie bei Verwendung einer Windows 10 Mobile-Gerät konfigurieren keine Fehlermeldung angezeigt. Die Richtlinie wird jedoch nicht wirksam wird.

> Verwenden Sie nicht diese Richtlinie in Windows 10, Version 1607 Geräte, stattdessen die neuen Richtlinien in [Windows-10, Version 1607 für aktualisieren Management](device-update-management.md#windows10version1607forupdatemanagement)aufgeführt. Sie können weiterhin DeferUpgradePeriod für Windows 10, Version 1511 Geräte verwenden.


<p style="margin-left: 20px">IT-Administratoren, zusätzliche Upgrade Verzögerungen für bis zu acht Monaten angeben können.

<p style="margin-left: 20px">Unterstützte Werte sind 0 bis 8, bezieht sich auf die Anzahl der Monate Upgrades zu verzögern.

<p style="margin-left: 20px">Wenn die Richtlinie "Specify Intranet Microsoft Update Service Location" aktiviert ist, haben Sie dann die "Defer Upgrades durch" sowie "Defer Aktualisierungen durch" und "Anhalten Updates und Upgrades" Einstellungen keine Auswirkung.

<p style="margin-left: 20px">Wenn die Richtlinie "Telemetrie zulassen" aktiviert ist, und der Optionen-Wert auf 0 festgelegt ist, haben Sie dann die "Defer Upgrades durch", "Defer Aktualisierungen durch" und "Pause Updates und Upgrades" Einstellungen keine Auswirkung.

<a href="" id="update-excludewudriversinqualityupdate"></a>**Update/ExcludeWUDriversInQualityUpdate**   
> **Hinweis**  Diese Richtlinie ist auf Windows 10 Pro, Windows 10 Enterprise, Windows 10 Education verfügbar.
> Da diese Richtlinie nicht gesperrt ist, erhalten Sie bei Verwendung einer Windows-10-Mobile-Gerät konfigurieren keine Fehlermeldung angezeigt. Jedoch dauert die Richtlinie nicht einent.

<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. IT-Administratoren Windows Update (WU) Treiber während der Aktualisierung ausschließen können.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – zulassen Windows Update-Treiber.
-   1 – Windows Update-Treiber ausschließen.

<a href="" id="update-pausedeferrals"></a>**Update/PauseDeferrals**  
> **Hinweis**  
> Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise
>
> Verwenden Sie nicht diese Richtlinie in Windows 10, Version 1607 Geräte, stattdessen die neuen Richtlinien in [Windows-10, Version 1607 für aktualisieren Management](device-update-management.md#windows10version1607forupdatemanagement)aufgeführt. Sie können weiterhin PauseDeferrals für Windows 10, Version 1511-Geräte verwenden.


<p style="margin-left: 20px">Ermöglicht es IT-Administratoren, Updates und Upgrades für bis zu fünf Wochen anzuhalten. Angehaltene Rückstellungen werden nach fünf Wochen zurückgesetzt.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – Rückstellungen nicht angehalten werden.
-   1 – Rückstellungen werden angehalten.

<p style="margin-left: 20px">Wenn die Richtlinie "Specify Intranet Microsoft Update Service Location" aktiviert ist, haben Sie dann die "Defer Upgrades durch" sowie "Defer Aktualisierungen durch" und "Anhalten Updates und Upgrades" Einstellungen keine Auswirkung.

<p style="margin-left: 20px">Wenn die Richtlinie "Telemetrie zulassen" aktiviert ist, und der Optionen-Wert auf 0 festgelegt ist, haben Sie dann die "Defer Upgrades durch", "Defer Aktualisierungen durch" und "Pause Updates und Upgrades" Einstellungen keine Auswirkung.

<a href="" id="update-pausefeatureupdates"></a>**Update/PauseFeatureUpdates**   
> **Hinweis**  Diese Richtlinie ist auf Windows 10 Pro, Windows 10 Enterprise, Windows 10 Education verfügbar.
<p style="margin-left: 20px">Da diese Richtlinie nicht gesperrt ist, erhalten Sie bei Verwendung einer Windows 10 Mobile-Gerät konfigurieren keine Fehlermeldung angezeigt. Die Richtlinie wird jedoch nicht wirksam wird.


<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Ermöglicht es IT-Administratoren Feature Updates für bis zu 60 Tage Anhalten aus.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – Feature Updates werden nicht angehalten.
-   1 – Feature Updates werden angehalten, 60 Tage oder bis Wert auf 0 festlegen, je nachdem, was stattfindet.

<a href="" id="update-pausequalityupdates"></a>**Update/PauseQualityUpdates**  
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise


<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Ermöglicht es IT-Administratoren Qualität Updates zu unterbrechen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – Qualität Updates nicht angehalten werden.
-   1 – Qualität Updates werden angehalten 35 Tage oder bis Wert wieder auf 0 festlegen, je nachdem, welche stattfindet.

<a href="" id="update-requiredeferupgrade"></a>**Update/RequireDeferUpgrade**  
> **Hinweis**  
> Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise
>
> Verwenden Sie nicht diese Richtlinie in Windows 10, Version 1607 Geräte, stattdessen die neuen Richtlinien in [Windows-10, Version 1607 für aktualisieren Management](device-update-management.md#windows10version1607forupdatemanagement)aufgeführt. Sie können weiterhin RequireDeferUpgrade für Windows 10, Version 1511-Geräte verwenden.


<p style="margin-left: 20px">Ermöglicht der IT-Administrator, um ein Gerät auf CBB Zug festzulegen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – Ruft Benutzer aus der aktuellen Zweig Upgrades ab.
-   1 – Benutzer ruft Upgrades aus der aktuellen Zweig for Business ab.

<a href="" id="update-requireupdateapproval"></a>**Update/RequireUpdateApproval**  

> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise

<br>

> **Hinweis**  Wenn Sie zuvor die Richtlinie **Update/PhoneUpdateRestrictions** in früheren Versionen von Windows verwendet, ist es veraltet. Verwenden Sie stattdessen diese Richtlinie.


<p style="margin-left: 20px">Ermöglicht der IT-Administrator, um die Updates zu beschränken, die auf einem Gerät, um nur die auf einer Updateliste Genehmigung installiert sind. Es ermöglicht der IT, akzeptieren den Endbenutzer-Lizenzvertrag (EULA) zugeordnet des genehmigten Updates im Namen der Endbenutzer. EULAs zugelassen werden, nachdem ein Update genehmigt wird.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Get und ersetzen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht konfiguriert. Vom Gerät installiert alle anwendbaren Aktualisierungen.
-   1 – vom Gerät installiert nur die Updates, die entsprechenden und in der Liste der genehmigten Updates sind. Legen Sie diese Richtlinie auf 1, wenn IT möchte steuern die Bereitstellung von Updates auf Geräten, beispielsweise wenn die Tests vor der Bereitstellung erforderlich ist.

<a href="" id="update-scheduledinstallday"></a>**Update/ScheduledInstallDay**  
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise


<p style="margin-left: 20px">Ermöglicht der IT-Administrator den Tag der Installation des Updates zu planen.

<p style="margin-left: 20px">Der Datentyp ist eine Zeichenfolge.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Get hinzufügen, löschen, und Ersetzen Sie.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – täglich
-   1 – Sonntag
-   2 – Montag
-   3 – Dienstag
-   4 – Mittwoch
-   5 – Donnerstag
-   6 – Freitag
-   7 – Samstag

<a href="" id="update-scheduledinstalltime"></a>**Update/ScheduledInstallTime**  
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise


<p style="margin-left: 20px">Ermöglicht der IT-Administrator, um den Zeitplan für die Installation des Updates.

<p style="margin-left: 20px">Der Datentyp ist eine Zeichenfolge.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Get hinzufügen, löschen, und Ersetzen Sie.

<p style="margin-left: 20px">Unterstützte Werte sind 0 – 23, wobei 0 = 12 Uhr und 23 = 11 Uhr.

<p style="margin-left: 20px">Der Standardwert ist 3.

<a href="" id="update-updateserviceurl"></a>**Update/UpdateServiceUrl**   
> **Hinweis**  Diese Richtlinie steht auf Windows 10 Pro Windows 10 Enterprise, Windows 10 Education und Windows 10 Mobile Enterprise


<p style="margin-left: 20px">Ermöglicht das Gerät an einen WSUS-Server und Microsoft Update nicht auf Updates überprüfen. Dies ist nützlich, MDMs am Standort, die zur Aktualisierung von Geräten, die keine Verbindung zum Internet herstellen können.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Get und ersetzen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   Nicht konfiguriert. Das Gerät sucht nach Updates von Microsoft Update.
-   Legen Sie auf eine URL wie `http://abcd-srv:8530`. Das Gerät sucht nach Updates vom WSUS-Server an der angegebenen URL.

Beispiel

``` syntax
        <Replace>
            <CmdID>$CmdID$</CmdID>
            <Item>
                <Meta>
                    <Format>chr</Format>
                    <Type>text/plain</Type>
                </Meta>
                <Target>
                    <LocURI>./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl</LocURI>
                </Target>
                <Data>http://abcd-srv:8530</Data>
            </Item>
        </Replace>
```

<a href="" id="wifi-allowautoconnecttowifisensehotspots"></a>**WiFi/AllowAutoConnectToWiFiSenseHotspots**  
<p style="margin-left: 20px">Zulassen oder das Gerät automatisch eine Verbindung mit Wi-Fi Hotspots herstellen dürfen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="wifi-allowinternetsharing"></a>**WiFi/AllowInternetSharing**  
<p style="margin-left: 20px">Zulassen Sie oder verbieten Sie des Internet freigeben.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – lässt nicht die Verwendung von Internet Sharing.
-   1 (Standard) – ermöglichen die Verwendung von Internet Sharing.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="wifi-allowmanualwificonfiguration"></a>**WiFi/AllowManualWiFiConfiguration**  
<p style="margin-left: 20px">Zulassen oder Herstellen einer Verbindung mit Wi-Fi außerhalb MDM Server installiert Netzwerke nicht zulassen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – No Wi-Fi-Verbindung außerhalb MDM bereitgestellten Netzwerk zulässig ist.
-   1 (Standard) – Hinzufügen von neuen Netzwerk SSIDs außerhalb der bereits MDM bereitgestellt Schriftarten zulässig ist.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

> **Hinweis**  Durch Festlegen dieser Richtlinie löscht alle zuvor installierten Benutzer konfiguriert und Wi-Fi Sinne Wi-Fi Profile vom Gerät aus. Bestimmte Wi-Fi-Profile, die keine Benutzer konfiguriert sind noch Wi-Fi Sinne kann nicht gelöscht werden. Darüber hinaus werden nicht alle nicht MDM Profile vollständig gelöscht.


<a href="" id="wifi-allowwifi"></a>**WiFi/AllowWiFi**  
<p style="margin-left: 20px">Zulassen Sie oder verweigern Sie Wi-Fi-Verbindung.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht Wi-Fi-Verbindung zulässig ist.
-   1 (Standard) – ist Wi-Fi-Verbindung zulässig.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<a href="" id="wifi-allowwifihotspotreporting"></a>**WiFi/AllowWiFiHotSpotReporting**  
<p style="margin-left: 20px">Diese Richtlinie ist veraltet.

<a href="" id="wifi-wlanscanmode"></a>**WiFi/WLANScanMode**  
<p style="margin-left: 20px">Ermöglichen eines Unternehmens zur Steuerung das WLAN-Scan Verhalten und wie aggressiv Geräte aktiv für Wi-Fi-Netzwerke angeschlossene Geräte abrufen überprüft werden soll.

<p style="margin-left: 20px">Unterstützte Werte sind 0-500, wobei 100 = normale Überprüfung Häufigkeit und 500 = niedriger Scanhäufigkeit.

<p style="margin-left: 20px">Der Standardwert ist 0.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Get hinzufügen, löschen, und Ersetzen Sie.

<a href="" id="windowsinkworkspace-allowwindowsinkworkspace"></a>**WindowsInkWorkspace/AllowWindowsInkWorkspace**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Gibt an, ob der Benutzer den Arbeitsbereich Freihand zugreifen kann.

<p style="margin-left: 20px">Werttyp ist int. In der folgenden Liste sind die unterstützten Werte:

-   0 – ist Zugriff auf ink-Arbeitsbereich deaktiviert. Das Feature ist deaktiviert.
-   1 – Freihand Workspace ist aktiviert (Funktion ist aktiviert), aber der Benutzer kann nicht über den Sperrbildschirm darauf zugreifen.
-   2 (Standard) - Freihand Workspace ist aktiviert (Funktion ist aktiviert), und der Benutzer kann über den Sperrbildschirm Verwendungsweise.

<a href="" id="windowsinkworkspace-allowsuggestedappsinwindowsinkworkspace"></a>**WindowsInkWorkspace/AllowSuggestedAppsInWindowsInkWorkspace**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Empfohlene app Vorschläge im Arbeitsbereich Freihand anzeigen.

<p style="margin-left: 20px">Werttyp ist Bool. In der folgenden Liste sind die unterstützten Werte:

-   0 – sind app Vorschläge nicht zulässig.
-   1 (Standard) - app Vorschläge zulassen.

<a href="" id="wirelessdisplay-allowprojectiontopc"></a>**WirelessDisplay/AllowProjectionToPC**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Zulassen Sie oder Sperren Sie das Deaktivieren der Projektion auf einem PC.

<p style="margin-left: 20px">Wenn Sie es auf 0 (null) festlegen, PC ist nicht sichtbar, und Sie können nicht darauf project. Wenn Sie es auf 1 festgelegt, Ihr PC sichtbar ist, und Sie können es über den Sperrbildschirm Projekt. Der Benutzer verfügt über eine Option, um immer aktiviert oder deaktiviert mit Ausnahme der manuellen Start zu aktivieren. In PCs teilnehmen, die Miracast unterstützen, nachdem die Richtlinie angewendet wird können überprüfen Sie die Einstellung aus der Benutzeroberfläche in **Einstellungen** &gt; **System** &gt; **Projecting mit diesem PC**.

<p style="margin-left: 20px">Werttyp ist Integer. Gültige Wert:

-   0 - Projektion an PC nicht zulässig. Immer deaktiviert, und der Benutzer nicht aktivieren.
-   1 (Standard) - ist Projektion PC zulässig ist. Nur über den Sperrbildschirm aktiviert.

<a href="" id="wirelessdisplay-requirepinforpairing"></a>**WirelessDisplay/RequirePinForPairing**  
<p style="margin-left: 20px">In Windows 10, Version 1607 hinzugefügt. Zulassen Sie oder verweigern Sie-Anforderung für eine PIN-NUMMER für die Bildung von.

<p style="margin-left: 20px">Wenn Sie dies zu aktivieren, ist das paarungs signaturzeremonie für neue Geräte immer eine PIN erforderlich. Wenn Sie diese Eigenschaft deaktivieren oder nicht konfigurieren, ist eine PIN nicht für die Bildung von erforderlich. In PCs teilnehmen, die Miracast unterstützen, nachdem die Richtlinie angewendet wird können überprüfen Sie die Einstellung aus der Benutzeroberfläche in **Einstellungen** &gt; **System** &gt; **Projecting mit diesem PC**.

<p style="margin-left: 20px">Werttyp ist Integer. Gültige Wert:

-   0 (Standard) - PIN ist nicht erforderlich.
-   1 – PIN ist erforderlich.

## <a name="examples"></a>Beispiele

Legen Sie die minimale Kennwortlänge auf 4 Zeichen.

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Replace>
            <CmdID>$CmdID$</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/Policy/Config/DeviceLock/MinDevicePasswordLength</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">int</Format>
                </Meta>
                <Data>4</Data>
            </Item>
        </Replace>
        <Final/>
    </SyncBody>
</SyncML>
```

NFK nicht zulassen.

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Replace>
            <CmdID>$CmdID$</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/Policy/Config/Connectivity/AllowNFC</LocURI>
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

## <a name="a-href-idstartlayout-examplesastartstartlayout-examples"></a><a href="" id="startlayout-examples"></a>Start-/StartLayout-Beispiele

### <a name="a-href-idgenerating-a-layout-agenerating-a-layout"></a><a href="" id="generating-a-layout-"></a>Generieren eines Layouts

Die einfachste Möglichkeit zum Generieren eines Layouts werden das Start-Layout auf einem PC festgelegt, und führen Sie das PowerShell-Cmdlet **Export-StartLayout**ab.

` > Export-StartLayout -path c:\users\<`*Sie*`>\desktop\startlayout.xml`

Beispiel-Layout mit dem Cmdlet generiert

``` syntax
<LayoutModificationTemplate Version="1" xmlns="http://schemas.microsoft.com/Start/2014/LayoutModification">
  <DefaultLayoutOverride>
    <StartLayoutCollection>
      <defaultlayout:StartLayout GroupCellWidth="6" xmlns:defaultlayout="http://schemas.microsoft.com/Start/2014/FullDefaultLayout">
        <start:Group Name="quick links" xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout">
          <start:Tile Size="2x2" Column="4" Row="4" TileID="903d2b5e-807b-4c7a-8362-0fcc184f97f7" AppUserModelID="windows.immersivecontrolpanel_cw5n1h2txyewy!microsoft.windows.immersivecontrolpanel"/>
          <start:Tile Size="4x4" Column="0" Row="0" TileID="ad99e7e3-3929-4e54-850c-0956e6dc6296" AppUserModelID="Microsoft.BingWeather_8wekyb3d8bbwe!App"/>
          <start:Tile Size="4x4" Column="0" Row="0" TileID="e86b4425-e28e-4e59-abeb-39316c1cd0eb" AppUserModelID="Microsoft.BingNews_8wekyb3d8bbwe!AppexNews"/>
          <start:Tile Size="2x2" Column="4" Row="4" TileID="37fe8c50-8b37-41e2-9d8b-f8915ef2b89b" AppUserModelID="Microsoft.WindowsCalculator_8wekyb3d8bbwe!App"/>
        </start:Group>
        <start:Group Name="LOB apps" xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout">
          <start:Tile Size="2x2" Column="4" Row="4" TileID="10c72642-ef27-4890-8d3b-f5a4b10b2611" AppUserModelID="CmModernAppv.01_g4ype1skzj3jy!App"/>
          <start:DesktopApplicationTile Size="2x2" Column="0" Row="0" DesktopApplicationID="wpsh..tion_0000000000000000_ea68d408322b5ed8"/>
          <start:Tile Size="2x2" Column="2" Row="2" TileID="68a2c085-a2a5-4849-a3e5-c5f8bd736b8f" AppUserModelID="Microsoft.CorporateAppCenter_8wekyb3d8bbwe!App"/>
        </start:Group>
        <start:Group Name="comms" xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout">
          <start:Tile Size="4x2" Column="0" Row="0" TileID="a39d270e-d013-40a9-879d-eb563c019a4f" AppUserModelID="microsoft.windowscommunicationsapps_8wekyb3d8bbwe!microsoft.windowslive.mail"/>
          <start:Tile Size="4x4" Column="0" Row="0" TileID="293e8dd8-c33d-4797-997e-f646902d1e56" AppUserModelID="microsoft.windowscommunicationsapps_8wekyb3d8bbwe!microsoft.windowslive.calendar"/>
          <start:Tile Size="2x2" Column="4" Row="4" TileID="2f5a81f5-7f85-42c9-88f7-dd41aa9609f7" AppUserModelID="Microsoft.People_8wekyb3d8bbwe!x4c7a3b7dy2188y46d4ya362y19ac5a5805e5x"/>
        </start:Group>
        <start:Group Name="Office" xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout">
          <start:DesktopApplicationTile Size="2x2" Column="2" Row="2" DesktopApplicationID="Microsoft.Office.lync.exe.15"/>
          <start:Tile Size="2x2" Column="4" Row="4" TileID="337be122-44b3-4215-8d6f-75f29af5a722" AppUserModelID="Microsoft.Office.OneNote_8wekyb3d8bbwe!microsoft.onenoteim"/>
          <start:DesktopApplicationTile Size="2x2" Column="0" Row="0" DesktopApplicationID="Microsoft.Office.OUTLOOK.EXE.15"/>
          <start:DesktopApplicationTile Size="2x2" Column="0" Row="0" DesktopApplicationID="Microsoft.Office.EXCEL.EXE.15"/>
          <start:DesktopApplicationTile Size="2x2" Column="2" Row="2" DesktopApplicationID="Microsoft.Office.ONENOTE.EXE.15"/>
          <start:DesktopApplicationTile Size="2x2" Column="4" Row="4" DesktopApplicationID="Microsoft.Office.POWERPNT.EXE.15"/>
        </start:Group>
        <start:Group Name="Edge pinned shortcuts" xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout">
          <start:SecondaryTile AppUserModelID="Microsoft.Windows.Edge_cw5n1h2txyewy!Microsoft.Edge.Edge" TileID="-9513911450" DisplayName="Bing" Size="2x2" Column="0" Row="0" Arguments="-contentTile -formatVersion 0x00000003 -pinnedTimeLow 0x36a8c2e4 -pinnedTimeHigh 0x01d0919b -securityFlags 0x00000000 -tileType 0x00000000 -url 0x00000014 http://www.bing.com/" Square150x150LogoUri="ms-appdata:///local/PinnedTiles/-9513911450/lowres.png" Wide310x150LogoUri="ms-appx:///" ShowNameOnSquare150x150Logo="true" ShowNameOnWide310x150Logo="true" BackgroundColor="#7fffffff"/>
          <start:SecondaryTile AppUserModelID="Microsoft.Windows.Edge_cw5n1h2txyewy!Microsoft.Edge.Edge" TileID="-2360074010" DisplayName="msn" Size="2x2" Column="2" Row="2" Arguments="-contentTile -formatVersion 0x00000003 -pinnedTimeLow 0xec458ccc -pinnedTimeHigh 0x01d091a0 -securityFlags 0x00000000 -tileType 0x00000000 -url 0x00000013 http://www.msn.com/" Square150x150LogoUri="ms-appdata:///local/PinnedTiles/-2360074010/hires.png" Wide310x150LogoUri="ms-appx:///" ShowNameOnSquare150x150Logo="true" ShowNameOnWide310x150Logo="true" BackgroundColor="#7fffffff"/>
          <start:SecondaryTile AppUserModelID="Microsoft.Windows.Edge_cw5n1h2txyewy!Microsoft.Edge.Edge" TileID="-21368412090" DisplayName="The Verge" Size="2x2" Column="4" Row="4" Arguments="-pinnedSite -contentTile -formatVersion 0x00000003 -pinnedTimeLow 0x00bad87b -pinnedTimeHigh 0x01d091a1 -securityFlags 0x00000000 -tileType 0x00000000 -url 0x00000018 http://www.theverge.com/" Square150x150LogoUri="ms-appdata:///local/PinnedTiles/-21368412090/squaretile.png" Wide310x150LogoUri="ms-appdata:///local/PinnedTiles/-21368412090/widetile.png" ShowNameOnSquare150x150Logo="true" ShowNameOnWide310x150Logo="true" BackgroundColor="#7fffffff"/>
        </start:Group>
        <start:Group Name="dev tools" xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout">
          <start:DesktopApplicationTile Size="2x2" Column="0" Row="0" DesktopApplicationID="{1AC14E77-02E7-4E5D-B744-2EB1AE5198B7}\cmd.exe"/>
          <start:DesktopApplicationTile Size="2x2" Column="2" Row="2" DesktopApplicationID="{D65231B0-B2F1-4857-A4CE-A8E7C6EA7D27}\WindowsPowerShell\v1.0\powershell.exe"/>
        </start:Group>
      </defaultlayout:StartLayout>
    </StartLayoutCollection>
  </DefaultLayoutOverride>
</LayoutModificationTemplate>
```

### <a name="understanding-the-schema"></a>Grundlegendes zum schema

Im vorherigen Beispiel wird das **DefaultLayoutOverride** -Element verwendet, um ein Layout anzugeben, die das Standardlayout Start überschreibt. Es enthält einen **StartLayoutCollection**. **StartLayoutCollection** enthält eine **StartLayout**, die einer Sammlung von **Gruppen** , die wiederum von **Kacheln** oder **DesktopApplicationTiles**bestehen, besteht.

### <a name="manually-creating-a-layout"></a>Manuelles Erstellen eines Layouts

Bei Elementen mit **Kachel** kann der **AppUserModelID** mit den PowerShell-Cmdlet **Get-StartApps**abgerufen werden. Die app muss installiert sein, um diese Informationen abzurufen.

Für **DesktopApplicationTile** Elemente kann die **DesktopApplicationID** mit dem PowerShell-Cmdlet **Get-StartApps**abgerufen werden. Die app muss installiert sein, um diese Informationen abzurufen.

### <a name="secondary-tiles"></a>Sekundäre Kacheln

Beim Erstellen eines Layouts müssen Sie einige besondere Hinweise sekundäre Kacheln. Im Allgemeinen ist die einfachste Möglichkeit, eine **SecondaryTile** ordnungsgemäß angegeben zum Erzeugen mithilfe des **Export-StartLayout** PowerShell-Cmdlets wie oben angegeben.

> **Hinweis**  Apps, die über ausreichend Informationen in ihrer sekundären Kacheln Codieren nicht kann möglicherweise nicht in der Richtlinie **StartLayout** effektiv verwendet werden.


### <a name="generic-webpage-shortcuts"></a>Generische Webseite Tastenkombinationen

Der einfachste Mechanismus zum Erstellen einer Verknüpfung zu einer Webseite ist eine URL-Datei verwendet. Dies kann manuell durch Angabe der URL in das Attribut **DesktopApplicationID** Layoutdatei hinzugefügt.

``` syntax
<start:DesktopApplicationTile Size="2x2" Column="0" Row="0" DesktopApplicationID="www.bing.com" />
```

### <a name="a-href-idmicrosoft-edge-secondary-tiles-amicrosoft-edge-secondary-tiles"></a><a href="" id="microsoft-edge-secondary-tiles-"></a>Microsoft Edge sekundäre Kacheln

Dies können mithilfe des **Export-StartLayout** -PowerShell-Cmdlets wie oben angegeben generiert werden. Das folgende Beispiel zeigt eine generierte sekundäre Kachel:

``` syntax
<start:SecondaryTile 
    AppUserModelID="Microsoft.Windows.Edge_cw5n1h2txyewy!Microsoft.Edge.Edge" 
    TileID="-9513911450" 
    DisplayName="Bing" 
    Size="2x2" 
    Column="0" 
    Row="0" 
    Arguments="-contentTile -formatVersion 0x00000003 -pinnedTimeLow 0x36a8c2e4 -pinnedTimeHigh 0x01d0919b -securityFlags 0x00000000 -tileType 0x00000000 -url 0x00000014 http://www.bing.com/" Square150x150LogoUri="ms-appdata:///local/PinnedTiles/-9513911450/lowres.png" 
    Wide310x150LogoUri="ms-appx:///" 
    ShowNameOnSquare150x150Logo="true" 
    ShowNameOnWide310x150Logo="true" 
    BackgroundColor="#7fffffff" 
  />
```

## <a name="related-topics"></a>Verwandte Themen

[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 






