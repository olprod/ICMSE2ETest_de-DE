---
title: Erstellen eines benutzerdefinierten Konfiguration-Dienstanbieters
description: Erstellen eines benutzerdefinierten Konfiguration-Dienstanbieters
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0cb37f03-5bf2-4451-8276-23f4a1dee33f
ms.openlocfilehash: eb2d7a0ec76b770246f5d3263e528f326c9187c3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-a-custom-configuration-service-provider"></a>Erstellen eines benutzerdefinierten Konfiguration-Dienstanbieters

Mobiles Gerät OEMs kann benutzerdefinierte Konfiguration Dienstanbieter Geräte erstellen. Ein Konfigurationsdienstanbieter enthält eine Schnittstelle zum Erstellen, bearbeiten und Löschen von Knoten und den Knoten selbst. Jeder Knoten enthält Daten für einen Registrierungswert und unterstützen können optional abrufen, festlegen und delete-Operationen.

Um eine benutzerdefinierte Konfiguration-Dienstanbieter zu entwerfen, muss der OEM die folgenden Schritte ausführen:

1.  Einrichten von Knoten Semantik
2.  Die Konfiguration des Dienstanbieters Unterstruktur Shape
3.  Wählen Sie ein Transactioning-Schema für jeden Knoten
4.  Bestimmen der Knotenvorgänge

Weitere Informationen finden Sie unter [Entwerfen eines benutzerdefinierten Konfiguration-Dienstanbieters](design-a-custom-windows-csp.md).

Um eine benutzerdefinierte Konfiguration-Dienstanbieter zu schreiben, muss der OEM die folgenden Schnittstellen implementieren:

-   [IConfigServiceProvider2](iconfigserviceprovider2.md) (einer pro Configuration-Dienstanbieter)

-   [ICSPNode](icspnode.md) (eine pro Knoten)

-   [ICSPNodeTransactioning](icspnodetransactioning.md) (optional, nur intern ungeachtet Knoten)

-   [ICSPValidate](icspvalidate.md) (optional, für die Benutzeroberfläche nur)

Dieser Code muss in einer einzigen DLL-Datei kompiliert und wie unter "Hinzufügen von Inhalt zu einem Paket" in [Erstellen von Paketen](https://msdn.microsoft.com/en-us/library/windows/hardware/dn756642)mit einem Paket hinzugefügt werden. Beim diesen Code schreiben, können OEMs registrierungseinstellungen und Dateien in den folgenden Orten gespeichert.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Dateispeicherort</strong></p></td>
<td><p>%DataDrive%\SharedData\OEM\CSP\</p></td>
</tr>
<tr class="even">
<td><p><strong>Speicherort der Registrierung</strong></p></td>
<td><p>$(HKLM. SOFTWARE) \OEM\CSP\</p></td>
</tr>
</tbody>
</table>


Beispiele zum Ausführen allgemeiner Aufgaben wie beispielsweise einen Knoten hinzufügen, ersetzen Wert des Knotens, Wert des Knotens Abfragen oder das Aufzählen von einem Knoten untergeordnete Elemente finden Sie [Beispiele für das Schreiben eines benutzerdefinierten Konfiguration Dienstanbieters](samples-for-writing-a-custom-configuration-service-provider.md).

Um den Konfigurations-Dienstanbieter als COM-Objekt zu registrieren, müssen Sie den folgenden Registrierungsschlüssel Ihr Paket hinzufügen. Dieser Schritt ist erforderlich. Ersetzen Sie im folgenden Beispiel *UniqueCSPguid* durch eine neue, eindeutige CLSID für diesen Zweck generiert. Ersetzen Sie *DLL-Name* mit dem Namen der DLL-Datei, die für Ihren Dienstanbieter für die Konfiguration den Code enthält ein.

``` syntax
<RegKeys>
    <RegKey KeyName="$(HKCR.CLASSES)\CLSID\{uniqueCSPguid}\InprocServer32">
        <RegValue Name="@" Type="REG_SZ" Value="dllName.dll" />
    </RegKey>
</RegKeys>
```

Um die Konfigurationsdienstanbieter ConfigManager2 registrieren, müssen Sie den folgenden Registrierungsschlüssel Ihr Paket hinzufügen. Dieser Schritt ist erforderlich. Ersetzen Sie im folgenden Beispiel *DLL-Name* mit dem Namen des Dienstanbieters Konfiguration (der Name des Stammknotens). Ersetzen Sie *UniqueCSPguid* mit demselben *UniqueCSPguid* -Wert wie im vorherigen Beispiel.

``` syntax
<RegKeys>
   <RegKey KeyName="$(HKLM.SOFTWARE)\Microsoft\Provisioning\CSPs\.\Vendor\OEM\{Name}">
       <RegValue Name="@" Value="{uniqueCSPguid}" Type="REG_SZ"/>
   </RegKey>
</RegKeys>
```

Um den Konfigurations-Dienstanbieter aus WAP XML zugreifen zu können, müssen Sie ihn mit der WAP Datenverarbeitung Einheit registrieren, indem Sie den folgenden Registrierungsschlüssel in Ihr Paket festlegen. Ersetzen Sie *Name* mit dem Namen des Dienstanbieters Konfiguration. Lassen Sie den GUID-Wert genau wie geschrieben hier.

``` syntax
<RegKeys>
   <RegKey KeyName="$(HKLM.SOFTWARE)\Classes\Name">
       <RegValue Name="WAPNodeProcessor" Value="{FB11047A-4051-4d1d-9DCA-C80C5DF98D70}" 
          Type="REG_SZ"/>
   </RegKey>
</RegKeys>
```

 






