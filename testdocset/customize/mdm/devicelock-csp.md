---
title: DeviceLock CSP
description: DeviceLock CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9a547efb-738e-4677-95d3-5506d350d8ab
ms.openlocfilehash: c9f3e94462131bd5447a0f6abf0ccec2841d92bc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicelock-csp"></a>DeviceLock CSP


Dienstanbieter DeviceLock Konfiguration wird von der Enterprise-Verwaltungsserver so konfigurieren Sie Gerätesperre weiterführende Richtlinien. Dieses Dienstanbieters Konfiguration wird von einem Enterprise-Management-Server unterstützt.

> **Hinweis**   Windows 10 Mobile wird DeviceLock CSP für die Abwärtskompatibilität unterstützt. Für Windows-10-Geräte sollten Sie die [Richtlinie CSP](policy-configuration-service-provider.md) für verschiedene Geräte sperreinstellungen verwenden. Sie können weiterhin DeviceLock CSP für Windows Phone 8.1 und Windows Phone 8.1 GDR-Geräte verwenden. DeviceLock CSP werden einige Zeit in der Zukunft veraltet sein.

 

Die Einstellung DevicePasswordEnabled muss auf 0 (Gerätekennworts ist aktiviert) festgelegt werden, für die folgenden Einstellungen wirksam werden:

-   AllowSimpleDevicePassword
-   MinDevicePasswordLength
-   AlphanumericDevicePasswordRequired
-   MaxDevicePasswordFailedAttempts
-   MaxInactivityTimeDeviceLock
-   MinDevicePasswordComplexCharacters

Die folgende Abbildung zeigt den DeviceLock Konfigurationsdienstanbieter im Strukturformat dar.

![Devicelock csp](images/provisioning-csp-devicelock.png)

<a href="" id="provider"></a>**Anbieter**  
Erforderlich. Ein interior Knoten um alle Anbieter für die Richtlinie zu gruppieren. Bereich wird dauerhaft gelöscht. Unterstützte Vorgang ist Get.

<a href="" id="---------------providerid"></a>***ProviderID***  
Optional Den Knoten mit dem konfigurierten Verwaltungsserver ProviderID aus. In Windows Phone 8 wird nur ein Enterprise-Verwaltungsserver unterstützt. D. h., sollte nur ein *ProviderID* Knoten vorhanden sein. Exchange ActiveSync-Richtlinien festlegen von Exchange werden durch das Sync-Client separat gespeichert. Bereich ist dynamisch. Die in der folgenden Vorgänge werden unterstützt:

-   **Hinzufügen** - die Verwaltung berücksichtigt werden, um die Konfiguration Service Provider-Struktur hinzufügen.
-   **Löschen** : Löschen aller Richtlinien durch dieses Konto festgelegt. In Enterprise Unenrollment konnte dieser Befehl verwendet werden, für das Entfernen der Werte vom Enterprise-Verwaltungsserver festgelegt.
-   **Get** - Rückgabe aller Richtlinien vom Verwaltungsserver festgelegt.

> **Hinweis**   Der Wert kann nicht geändert werden, nachdem er hinzugefügt wird. Der Befehl **Ersetzen** wird nicht unterstützt.

 

<a href="" id="providerid-devicepasswordenabled"></a>***ProviderID*/DevicePasswordEnabled**  
Optional Ein Ganzzahlwert, der angibt, ob Gerätesperre aktiviert ist. Mögliche Werte sind die folgenden:

-   0 – ist Gerätesperre aktiviert.
-   1 (Standard) - Gerätesperre nicht aktiviert.

Der Bereich ist dynamisch.

Unterstützte Vorgänge sind Get, hinzufügen, und ersetzen.

<a href="" id="providerid-allowsimpledevicepassword"></a>***ProviderID*/AllowSimpleDevicePassword**  
Optional Ein Ganzzahlwert, der angibt, ob einfache Kennwörter, z. B. "1111" oder "1234", zulässig sind. Mögliche Werte für diesen Knoten sind eine der folgenden:

-   0 – nicht zulässig.
-   1 (Standard) - zulässig.

Ungültige Werte werden als ein Konfigurationsfehler behandelt. Dynamisch ist des Bereichs.

Unterstützte Vorgänge sind Get, hinzufügen, und ersetzen.

<a href="" id="providerid-mindevicepasswordlength"></a>***ProviderID*/MinDevicePasswordLength**  
Optional Ein Ganzzahlwert, der die minimale Anzahl von Zeichen erforderlich sind, in die PIN-NUMMER angibt. Gültige Werte sind 4 bis 18 an. Der Standardwert ist 4. Ungültige Werte werden als ein Konfigurationsfehler behandelt. Dynamisch ist des Bereichs.

Unterstützte Vorgänge sind Get, hinzufügen, und ersetzen.

<a href="" id="providerid-alphanumericdevicepasswordrequired"></a>***ProviderID*/AlphanumericDevicePasswordRequired**  
Optional Ein Ganzzahlwert, der angibt, die Komplexität der das Kennwort oder die PIN-NUMMER zulässig.

Gültige Werte sind folgende:

-   0 – Alphanumerisches Kennwort erforderlich
-   1 – Benutzer können ein Kennwort numerische oder alphanumerische auswählen.
-   2 - Benutzer können kein Kennwort, Kennwort numerische oder Alphanumerisches Kennwort auswählen

Ungültige Werte werden als ein Konfigurationsfehler behandelt. Dynamisch ist des Bereichs.

Unterstützte Vorgänge sind Get, hinzufügen, und ersetzen.

<a href="" id="providerid-devicepasswordexpiration"></a>***ProviderID*/DevicePasswordExpiration**  
Veraltet in Windows 10.

<a href="" id="providerid-devicepasswordhistory"></a>***ProviderID*/DevicePasswordHistory**  
Veraltet in Windows 10.

<a href="" id="providerid-maxdevicepasswordfailedattempts"></a>***ProviderID*/MaxDevicePasswordFailedAttempts**  
Optional Ein Ganzzahlwert, der die Anzahl der zulässig ist, bevor das Gerät wird bereinigt werden Authentifizierungsfehler angibt. Gültige Werte sind 0 bis 999 an. Der Standardwert ist 0 (null) und gibt an, dass das Gerät wird nicht unabhängig von der Anzahl der Authentifizierungsfehler bereinigt werden.

Ungültige Werte werden als ein Konfigurationsfehler behandelt. Der Bereich ist dynamisch.

Unterstützte Vorgänge sind Get, hinzufügen, und ersetzen.

<a href="" id="providerid-maxinactivitytimedevicelock"></a>***ProviderID*/MaxInactivityTimeDeviceLock**  
Optional Ein Ganzzahlwert, der die Dauer (in Minuten), die das Gerät inaktiv sein angibt, bevor es mit Kennwortschutz gesperrt ist. Gültige Werte sind 0 bis 999. Der Wert 0 gibt an, dass kein Timeout angegeben ist. In diesem Fall gilt das maximale Bildschirm Timeout von der Benutzeroberfläche zulässig.

Ungültige Werte werden als ein Konfigurationsfehler behandelt. Dynamisch ist des Bereichs.

Unterstützte Vorgänge sind Get, hinzufügen, und ersetzen.

<a href="" id="providerid-mindevicepasswordcomplexcharacters"></a>***ProviderID*/MinDevicePasswordComplexCharacters**  
Optional Ein Ganzzahlwert, der die Anzahl der komplexe w (Groß-und Kleinbuchstaben, Zahlen und Interpunktion) erforderlichen Typen für ein sicheres Kennwort angibt. Gültige Werte sind 1 bis 4 für Mobile und 1 bis 3 für Desktop. Der Standardwert ist 1.

Ungültige Werte werden als ein Konfigurationsfehler behandelt. Der Bereich ist dynamisch.

Unterstützte Vorgänge sind Get, hinzufügen, und ersetzen.

<a href="" id="devicevalue"></a>**DeviceValue**  
Erforderlich. Eine permanente Knoten, der die Richtlinienwerte angewendet auf das Gerät gruppiert. Der Server kann Abfragen diesen Knoten, um zu ermitteln, welche Richtlinienwerte tatsächlich auf dem Gerät angewendet werden. Des Bereichs ist dauerhaft.

Unterstützte Vorgang ist Get.

<a href="" id="devicevalue-devicepasswordenable-----mindevicepasswordcomplexcharacters"></a>**DeviceValue/DevicePasswordEnable,..., MinDevicePasswordComplexCharacters**  
Erforderlich. Dieser Knoten enthält als **ProviderID** Knoten den gleichen Satz von Knoten der Richtlinie. Alle Knoten unter **DeviceValue** sind schreibgeschützt permanente Knoten. Jedem Knoten darstellt, der aktuellen Gerät für die Sperre. Eine ausführliche Beschreibung der einzelnen Richtlinien finden Sie unter den ***ProviderID*** Unterknoten Beschreibungen.

## <a name="oma-dm-examples"></a>Beispiele für OMA DM


Legen Sie Richtlinien für Geräte sperren:

``` syntax
<Atomic>
   <CmdID>13</CmdID>
   <Add>
      <CmdID>2</CmdID>
      <Item>
         <Target>
            <LocURI>
               ./Vendor/MSFT/DeviceLock/Provider/TestMDMServer/MaxDevicePasswordFailedAttempts
            </LocURI>
         </Target>
         <Meta>
            <Format xmlns="syncml:metinf">int</Format>
         </Meta>
         <Data>4</Data>
      </Item>
   </Add>
   <Add>
      <CmdID>3</CmdID>
      <Item>
         <Target>
            <LocURI>
               ./Vendor/MSFT/DeviceLock/Provider/TestMDMServer/DevicePasswordEnabled</LocURI>
         </Target>
         <Meta>
            <Format xmlns="syncml:metinf">int</Format>
         </Meta>
         <Data>0</Data>
      </Item>
   </Add>
   <Add>
      <CmdID>4</CmdID>
      <Item>
         <Target>
            <LocURI>
               ./Vendor/MSFT/DeviceLock/Provider/TestMDMServer/AllowSimpleDevicePassword
            </LocURI>
         </Target>
         <Meta>
            <Format xmlns="syncml:metinf">int</Format>
         </Meta>
         <Data>1</Data>
      </Item>
   </Add>
   <Add>
      <CmdID>5</CmdID>
      <Item>
         <Target>
            <LocURI>
               ./Vendor/MSFT/DeviceLock/Provider/TestMDMServer/MinDevicePasswordLength
            </LocURI>
         </Target>
         <Meta>
            <Format xmlns="syncml:metinf">int</Format>
         </Meta>
         <Data>5</Data>
      </Item>
   </Add>
   <Add>
      <CmdID>6</CmdID>
      <Item>
         <Target>
            <LocURI>
            ./Vendor/MSFT/DeviceLock/Provider/TestMDMServer/AlphanumericDevicePasswordRequired
            </LocURI>
         </Target>
         <Meta>
            <Format xmlns="syncml:metinf">int</Format>
         </Meta>
         <Data>1</Data>
      </Item>
   </Add>
   <Add>
      <CmdID>7</CmdID>
      <Item>
         <Target>
            <LocURI>
               ./Vendor/MSFT/DeviceLock/Provider/TestMDMServer/DevicePasswordExpiration
            </LocURI>
         </Target>
         <Meta>
            <Format xmlns="syncml:metinf">int</Format>
         </Meta>
         <Data>2</Data>
      </Item>
   </Add>
   <Add>
      <CmdID>8</CmdID>
      <Item>
         <Target>
            <LocURI>
               ./Vendor/MSFT/DeviceLock/Provider/TestMDMServer/DevicePasswordHistory
            </LocURI>
         </Target>
         <Meta>
            <Format xmlns="syncml:metinf">int</Format>
         </Meta>
         <Data>50</Data>
      </Item>
   </Add>
   <Add>
      <CmdID>9</CmdID>
      <Item>
         <Target>
            <LocURI>
               ./Vendor/MSFT/DeviceLock/Provider/TestMDMServer/MaxInactivityTimeDeviceLock
            </LocURI>
         </Target>
         <Meta>
            <Format xmlns="syncml:metinf">int</Format>
         </Meta>
         <Data>2</Data>
      </Item>
   </Add>
   <Add>
      <CmdID>10</CmdID>
      <Item>
         <Target>
            <LocURI>
            ./Vendor/MSFT/DeviceLock/Provider/TestMDMServer/MinDevicePasswordComplexCharacters
            </LocURI>
         </Target>
         <Meta>
            <Format xmlns="syncml:metinf">int</Format>
         </Meta>
         <Data>2</Data>
      </Item>
   </Add>
</Atomic>
```

## <a name="remarks"></a>Hinweise


Alle Knotenwerte, die unter dem **ProviderID** interior Knoten darstellen, vom Verwaltungsserver festgelegten Richtlinienwerte weisen.

-   Ein Befehl **Hinzufügen** oder **Ersetzen Sie** auf diesen Knoten zurückgegeben Erfolg in den folgenden Fällen:

    -   Der Wert wird auf dem Gerät tatsächlich angewendet.

    -   Der Wert wird auf das Gerät nicht angewendet, da das Gerät sichereren Wert bereits festgelegt wurde.

        Aus Gründen der Sicherheit entspricht das Gerät der Richtlinie an, die mindestens so sicher wie diejenige angefordert wird.

-   **Get** -Befehl auf diesen Knoten zurückgegeben, dass der Wert der Server auf das Gerät nach unten geschoben.

-   Ein Befehl **Ersetzen** ein Fehler auftritt, wird der Wert des Knotens wieder auf den Wert festgelegt, der ersetzt werden.

-   Wenn ein Befehl **Hinzufügen** ein Fehler auftritt, wird der Knoten nicht erstellt.

Der Wert für das Gerät kann über den Knoten unter dem **DeviceValue** interior Knoten abgefragt werden.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






