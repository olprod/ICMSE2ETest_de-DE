---
title: WindowsLicensing CSP
description: WindowsLicensing CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: E6BC6B0D-1F16-48A5-9AC4-76D69A7EDDA6
ms.openlocfilehash: a840ed9ffdaf6e6126fccf1259332fc143ead92c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windowslicensing-csp"></a>WindowsLicensing CSP


Der Dienstanbieter für WindowsLicensing-Konfiguration ist darauf ausgelegt, für die Lizenzierung von verwandten Verwaltungsszenarien. Derzeit ist der Bereich auf Edition Upgrades von Windows 10 beschränkt Desktop- und mobilen Geräten, wie Windows 10 Pro an Windows 10 des Unternehmens. Darüber hinaus enthält dieser CSP die Möglichkeit zum Aktivieren oder ändern Sie den Product Key der Windows-10-desktop-Geräte.

Das folgende Diagramm zeigt den WindowsLicensing Konfigurationsdienstanbieter in der Strukturformat.

![Windowslicensing Csp Diagramm](images/provisioning-csp-windowslicensing-th2.png)

<a href="" id="--vendor-msft-windowslicensing"></a>**./Vendor/MSFT/WindowsLicensing**  
Dies ist der Stammknoten für den Dienstanbieter für WindowsLicensing-Konfiguration.

Der unterstützte Vorgang ist Get.

<a href="" id="upgradeeditionwithproductkey"></a>**UpgradeEditionWithProductKey**  
Gibt einen Product Key für ein Upgrade Edition des Windows-10-Desktopgeräte ein.

> **Hinweis**   Upgrade-Vorgangs ist einen Neustart des Systems erforderlich.

 

Der Datumstyp ist eine chr.

Der unterstützte Vorgang ist Exec.

Wenn von einem MDM Server ein Product Key auf dem Gerät des Benutzers verschoben werden, verwenden den Product Key wird **changepk.exe** ausgeführt. Nach Abschluss wird eine Benachrichtigung an den Benutzer angezeigt, dass eine neue Version von Windows 10 verfügbar ist. Der Benutzer kann starten Sie dann ihr System manuell oder nach zwei Stunden das Gerät automatisch neu gestartet, um das Upgrade abzuschließen. Der Benutzer erhält eine Erinnerung 10 Minuten vor dem automatischen Neustart.

Nach dem Neustart des Geräts, wird der Edition Upgradeprozess abgeschlossen. Der Benutzer erhält eine Benachrichtigung über die erfolgreiche Aktualisierung.

> **Wichtig**  Das Upgrade Edition schlägt fehl, wenn eine andere Richtlinie einen Neustart des Systems erforderlich, die sind bei **changepk.exe** ausgeführt wird.

 

Wenn Sie ein Product Key in einem Paket provisioning eingegeben ist, und der Benutzer die Installation des Pakets beginnt, wird eine Benachrichtigung für den Benutzer angezeigt, dass das System neu gestartet werden, um die Installation des Pakets abzuschließen. Ausdrückliche Zustimmung des Benutzers, um den Vorgang fortsetzen, das Paket wird die Installation fortgesetzt und **changepk.exe** ausgeführt wird, verwenden den Product Key. Der Benutzer erhält eine Erinnerung 30 Sekunden vor dem Neustart automatisch.

Nach dem Neustart des Geräts, schließt der Upgradevorgang Edition ab. Der Benutzer erhält eine Benachrichtigung über die erfolgreiche Aktualisierung.

Dieser Knoten kann auch verwendet werden, aktivieren oder ändern einen Product Key auf eine bestimmte Edition von Windows-10-Desktopgerät, indem Sie einen Product Key eingeben. Aktivierung oder ändern einen Product Key erfordert einen Neustart nicht und ist der Prozess für den Benutzer im Hintergrund.

> **Wichtig**  Der eingegebene Product Key muss 29 Zeichen (d. h., sie sollten Bindestriche enthalten), andernfalls wird die Aktivierung, Aktualisierung Edition oder Product Key ändern auf Windows-10-Desktopgeräte fehl. Der Product Key wird von Microsoft Volume Licensing Service Center erworben werden. Ihre Organisation muss den Zugriff auf das Portal einen Volume Licensing Vertrag mit Microsoft verfügen.

 

Im folgenden sind gültige Edition Upgradepfade bei Verwendung dieser Knoten über eine MDM:

-   Windows 10 Enterprise, Education Windows 10
-   Windows-10-Homepage, um Windows 10 Bildungseinrichtungen
-   Windows 10 Pro 10 Windows Bildungseinrichtungen
-   Windows 10 Pro 10 Windows Enterprise

Aktivierung oder einen Product Key ändern kann bei den folgenden Editionen durchgeführt werden:

-   Windows 10 Bildungseinrichtungen
-   Windows 10 Enterprise
-   Windows-10-Startseite
-   Windows 10 Pro

<a href="" id="edition"></a>**Edition**  
Gibt einen Wert, der der desktop oder mobilen Geräte unter Windows 10 Edition zugeordnet ist. Übernehmen Sie den Wert in seine hexadezimale Entsprechung konvertiert und die GetProductInfo Funktion Seite auf MSDN Edition Informationen durchsuchen.

Der Datentyp ist ein int-Wert.

Der unterstützte Vorgang ist Get.

<a href="" id="status"></a>**Status**  
Gibt den Status einer Edition aktualisieren auf Windows 10 Desktop oder mobilen Geräten. Der Status entspricht einem der folgenden Werte:

-   0 = fehlgeschlagen
-   1 = Ausstehend
-   2 = in Bearbeitung
-   3 = abgeschlossen
-   4 = unbekannt

Der Datentyp ist ein int.

Der unterstützte Vorgang ist Get.

<a href="" id="upgradeeditionwithlicense"></a>**UpgradeEditionWithLicense**  
Stellt eine Lizenz für ein Upgrade Edition Windows 10 mobiler Geräte bereit.

> **Hinweis**  Diese Upgradeprozess erfordert keinen Neustart des Systems.

 

Der Datumstyp ist XML.

Der unterstützte Vorgang ist ausführen.

> **Wichtig**  Den Inhalt der XML-Datei Lizenz ordnungsgemäß geschützt werden müssen (d. h., es sollte nicht einfach sein einer kopierten XML), andernfalls die Aktualisierung Edition auf mobilen Geräten Windows 10 schlägt fehl. Weitere Informationen über die richtige escaping der Lizenz-XML-Datei finden Sie im Abschnitt 2.4 der [W3C XML-Spezifikation](http://www.w3.org/TR/xml/) . Die Lizenz-XML-Datei ist die Microsoft Volume Licensing Service Center erworben haben. Ihre Organisation muss einen Vertrag Volumenlizenzierung mit Microsoft den Zugriff auf das Portal verfügen.

 

Im folgenden sind gültige Edition Upgradepfade bei Verwendung dieser Knoten über eine MDM oder provisioning-Paket:

-   Windows 10 Mobileto Windows 10 Mobile Enterprise

<a href="" id="licensekeytype"></a>**LicenseKeyType**  
Gibt den Parametertyp von Windows 10 Geräte für Upgrade, Aktivierung oder Product Key ändern ein Edition verwendet.

-   Windows-10 für Desktopgeräte erfordern keinen Product Key.
-   Windows 10 Mobile Geräte ist eine XML-Datei für ein Upgrade Edition erforderlich.

Der Datentyp ist eine chr.

Der unterstützte Vorgang ist abrufen.

<a href="" id="checkapplicability"></a>**CheckApplicability**  
Gibt TRUE zurück, wenn der eingegebene Product Key für ein Upgrade Edition, Aktivierung verwendet werden kann, oder ändern Sie einen Product Key der Windows-10 für desktop-Geräte.

Der Datentyp ist eine chr.

Der unterstützte Vorgang ist Exec.

## <a name="syncml-examples"></a>Beispiele für SyncML


**CheckApplicability**

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.1">
  <SyncBody>
    <Exec>
    <CmdID>3</CmdID>
    <Item>
      <Target>
        <LocURI>./Device/Vendor/MSFT/WindowsLicensing/CheckApplicability</LocURI>
      </Target>
      <Meta>
        <Format xmlns="syncml:metinf">chr</Format>
      </Meta>
      <Data>XXXXX-XXXXX-XXXXX-XXXXX-XXXXX</Data> 
    </Item>
   </Exec>
   <Final/>
  </SyncBody>
</SyncML>
```

> **Hinweis** `XXXXX-XXXXX-XXXXX-XXXXX-XXXXX` Tag sollte in den **Daten** mit Ihren Product Key ersetzt werden.  

 

**Edition**

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.1">
  <SyncBody>
    <Get>
      <CmdID>17</CmdID>
        <Item>
          <Target>
            <LocURI>./Device/Vendor/MSFT/WindowsLicensing/Edition</LocURI>
          </Target>
        </Item>
    </Get>
    <Final/>
  </SyncBody>
</SyncML>
```

**LicenseKeyType**

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.1">
  <SyncBody>
    <Get>
      <CmdID>17</CmdID>
        <Item>
          <Target>
            <LocURI>./Device/Vendor/MSFT/WindowsLicensing/LicenseKeyType</LocURI>
          </Target>
        </Item>
    </Get>
    <Final/>
  </SyncBody>
</SyncML>
```

**Status**

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.1">
  <SyncBody>
    <Get>
      <CmdID>17</CmdID>
        <Item>
          <Target>
            <LocURI>./Device/Vendor/MSFT/WindowsLicensing/Status</LocURI>
          </Target>
        </Item>
    </Get>
    <Final/>
  </SyncBody>
</SyncML>
```

**UpgradeEditionWithProductKey**

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.1">
  <SyncBody>
    <Exec>
    <CmdID>3</CmdID>
    <Item>
      <Target>
        <LocURI>./Device/Vendor/MSFT/WindowsLicensing/UpgradeEditionWithProductKey</LocURI>
      </Target>
      <Meta>
        <Format xmlns="syncml:metinf">chr</Format>
      </Meta>
      <Data>XXXXX-XXXXX-XXXXX-XXXXX-XXXXX</Data> 
    </Item>
   </Exec>
   <Final/>
  </SyncBody>
</SyncML>
```

> **Hinweis** `XXXXX-XXXXX-XXXXX-XXXXX-XXXXX` Tag sollte in den **Daten** mit Ihren Product Key ersetzt werden.  

 

**UpgradeEditionWithLicense**

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.1">
  <SyncBody>
    <Exec>
      <CmdID>2</CmdID>
      <Item>
        <Target>
          <LocURI>./Device/Vendor/MSFT/WindowsLicensing/UpgradeEditionWithLicense</LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">chr</Format>
        </Meta>
        <Data><!-- XML ENCODED LICENSE GOES HERE --></Data>
      </Item>
    </Exec>
    <Final/>
  </SyncBody>
</SyncML>
```

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






