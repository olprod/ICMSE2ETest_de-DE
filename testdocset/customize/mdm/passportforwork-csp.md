---
title: PassportForWork CSP
description: "Der Dienstanbieter für PassportForWork Konfiguration wird verwendet, um Windows Hello für Unternehmen (früher Microsoft Passport für die Arbeit) bereitstellen."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3BAE4827-5497-41EE-B47F-5C071ADB2C51
ms.openlocfilehash: d123be19a7e01bf09773efb5fae094b6fa8b8597
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="passportforwork-csp"></a>PassportForWork CSP


Der Dienstanbieter für PassportForWork Konfiguration wird verwendet, um Windows Hello für Unternehmen (früher Microsoft Passport für die Arbeit) bereitstellen. Es können Sie bei Windows mit Ihrem Active Directory oder Azure Active Directory-Konto anmelden, und Ersetzen Sie Kennwörter, Smartcards und virtuelle Smart Karten.

> **Wichtige**  Beginnend mit Windows 10, Version 1607, dass alle Geräte nur eine zugeordnete PIN Windows Hello für Unternehmen. Dies bedeutet, dass PIN auf einem Gerät müssen die Richtlinien im PassportForWork CSP angegeben wird. Die angegebenen Werte haben Vorrang vor jeder Komplexitätsregeln über Exchange ActiveSync (EAS) oder die DeviceLock CSP festgelegt.

 

### <a name="user-configuration-diagram"></a>Benutzer-Konfigurationsdiagramm

Das folgende Diagramm zeigt den PassportForWork Konfigurationsdienstanbieter im Strukturformat dar.

![Passportforwork csp](images/provisioning-csp-passportforwork.png)

### <a name="device-configuration-diagram"></a>Gerät-Konfigurationsdiagramm

Das folgende Diagramm zeigt den PassportForWork Konfiguration-Dienstanbieter in der Strukturformat.

![Passportforwork Diagramm](images/provisioning-csp-passportforwork2.png)

<a href="" id="passportforwork"></a>**PassportForWork**  
Stammknoten für PassportForWork Konfiguration-Dienstanbieter.

<a href="" id="tenantid"></a>***TenantId***  
Der global eindeutigen Bezeichner (GUID) ohne geschweifte Klammern ({,}).

<a href="" id="tenantid-policies"></a>****TenantId/Außerkraftsetzungsrichtlinien**  
Knoten für die Definition der Windows Hello for Business-Richtlinieneinstellungen.

<a href="" id="tenantid-policies-usepassportforwork"></a>****TenantId/Richtlinien/UsePassportForWork**  
Boolescher Wert, der Windows Hello für Unternehmen als Methode zur Anmeldung bei Windows festgelegt.

Standardwert ist true. Wenn Sie diese Richtlinie auf False festlegen, kann nicht der Benutzer Windows Hello für Unternehmen mit Ausnahme der auf Mobiltelefonen Azure Active Directory verbunden bereitstellen, auf dem Bereitstellung erforderlich ist.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

<a href="" id="tenantid-policies-requiresecuritydevice"></a>****TenantId/Richtlinien/RequireSecurityDevice**  
Boolescher Wert, der ein Modul TPM (Trusted Platform) für Windows Hello für Unternehmen benötigt. TPM bietet einen zusätzliche Sicherheitsvorteil über Software, sodass darin gespeicherte Daten auf anderen Geräten verwendet werden können.

Standardwert ist false. Wenn Sie diese Richtlinie auf "true" festlegen, können nur Geräte mit einem verwendbar TPM Windows Hello für Unternehmen bereitstellen. Wenn Sie diese Richtlinie auf False festlegen, können alle Geräte bereitstellen Windows Hello für Unternehmens über Software, selbst wenn ein verwendbar TPM nicht vorhanden ist. Wenn Sie diese Einstellung nicht konfigurieren, können alle Geräte bereitstellen Windows Hello für Unternehmen Software verwenden, wenn das TPM funktioniert nicht oder nicht verfügbar ist.

Unterstützte Vorgänge sind Add, Get löschen, und ersetzen.

<a href="" id="tenantid-policies-usecertificateforonpremauth--only-for---device-vendor-msft-"></a>** *TenantId*/Policies/UseCertificateForOnPremAuth** (nur für ./Device/Vendor/MSFT)  
Boolescher Wert, mit der Windows Hello für Unternehmen von Zertifikaten auf Standortbasierte Ressourcen authentifizieren kann.

Wenn Sie diese Einstellung aktivieren, wird Windows Hello für Unternehmen warten, bis das Gerät eine Zertifikat Nutzlast vor der Bereitstellung einer PIN-NUMMER aus der Enterprise-Zertifizierungsstelle erhalten hat.

Wenn Sie deaktivieren oder diese Einstellung nicht konfigurieren, wird die PIN bereitgestellt werden, bei Anmeldung des Benutzers, ohne warten auf ein Zertifikat Nutzlast.

Unterstützte Vorgänge sind Add, Get löschen, und ersetzen.

<a href="" id="tenantid-policies-pincomplexity"></a>****TenantId/Richtlinien/PINComplexity**  
Knoten zum Definieren von PIN-Einstellungen.

<a href="" id="tenantid-policies-pincomplexity-minimumpinlength"></a>***TenantId*/Policies/PINComplexity/MinimumPINLength**  
Integer-Wert, der die Mindestanzahl der Zeichen für die Arbeit PIN erforderlich festgelegt. Standardwert ist 4. Die kleinste Zahl für diese Einstellung konfigurierbaren ist 4. Die größte Zahl konfigurierbaren kleiner als die Anzahl, die in der Einstellung Maximale PIN-Richtlinie oder die Anzahl 127 konfiguriert sein, je nachdem, was ist die niedrigste.

Wenn Sie diese Einstellung konfigurieren, muss die Arbeit PIN-Länge größer als oder gleich an diese Nummer. Wenn Sie deaktivieren oder diese Einstellung nicht konfigurieren, muss die Arbeit PIN-Länge größer als oder gleich 4.

> **Hinweis**  Wenn die für die PIN-Mindestlänge oben angegebenen nicht erfüllt sind, werden die Standardwerte für die maximale und minimale PIN-Länge verwendet werden.

 

Werttyp ist int. Unterstützte Vorgänge sind hinzufügen, abrufen, löschen und ersetzen.

<a href="" id="tenantid-policies-pincomplexity-maximumpinlength"></a>***TenantId*/Policies/PINComplexity/MaximumPINLength**  
Integer-Wert, der die maximale Anzahl der zulässigen Zeichen für die Arbeit PIN festlegt. Standardwert ist 127. Die größte Zahl für diese Einstellung konfigurierbaren ist 127. Die kleinste Zahl, die Sie konfigurieren können, muss größer als die Anzahl, die in der Einstellung Minimale PIN-Richtlinie oder die Nummer 4 konfiguriert werden, je nachdem, was ist größer.

Wenn Sie diese Einstellung konfigurieren, muss die Arbeit PIN-Länge kleiner oder gleich auf diese Nummer. Wenn Sie deaktivieren oder diese Einstellung nicht konfigurieren, muss die Arbeit PIN-Länge kleiner als oder gleich 127.

> **Hinweis**  Wenn die für die maximale Länge des PIN oben angegebenen nicht erfüllt sind, werden die Standardwerte für die maximale und minimale PIN-Länge verwendet werden.

 

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

<a href="" id="tenantid-policies-pincomplexity-uppercaseletters"></a>***TenantId*/Policies/PINComplexity/UppercaseLetters**  
Ganze Zahl, die die Verwendung von Großbuchstaben in der Windows Hello für Business PIN konfiguriert.

Gültige Werte:

-   0 – ermöglicht die Verwendung von Großbuchstaben in PIN-NUMMER.
-   1 – erfordert die Verwendung von mindestens einen Großbuchstaben in PIN-NUMMER.
-   2 - die Verwendung von Großbuchstaben in PIN-NUMMER lässt nicht zu werden.

Standardwert ist 2. Standardverhalten der PIN Komplexität ist, dass Ziffern erforderlich sind, und alle anderen Zeichensätzen sind nicht zulässig. Alle Zeichensätze sind zulässig, jedoch keine explizit erforderlich sind, wird das Standardverhalten des PIN Komplexität angewendet.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen und ersetzen.

<a href="" id="tenantid-policies-pincomplexity-lowercaseletters"></a>***TenantId*/Policies/PINComplexity/LowercaseLetters**  
Ganze Zahl, die die Verwendung von Kleinbuchstaben in der Windows Hello für Business PIN konfiguriert.

Gültige Werte:

-   0 – ermöglicht die Verwendung von Kleinbuchstaben in PIN-NUMMER.
-   1 – erfordert die Verwendung von mindestens einen Kleinbuchstaben in PIN-NUMMER.
-   2 - wird die Verwendung von Kleinbuchstaben PIN nicht zulassen.

Standardwert ist 2. Standardverhalten für PIN Komplexität ist Ziffern erforderlich sind, und alle anderen Zeichensätzen sind nicht zulässig. Alle Zeichensätze sind zulässig, jedoch keine explizit erforderlich sind, wird das Standardverhalten des PIN Komplexität angewendet.

Unterstützte Vorgänge sind Add, Get löschen, und ersetzen.

<a href="" id="tenantid-policies-pincomplexity-specialcharacters"></a>***TenantId*/Policies/PINComplexity/SpecialCharacters**  
Ganze Zahl, die die Verwendung von Sonderzeichen in der Windows Hello für Business PIN konfiguriert. Gültige Sonderzeichen für Windows Hello für Business PIN Gesten enthalten:! " \# $ % & ' ( ) \* + , - . / : ; &lt; = &gt; ? @\[ \\ \] ^ \_ \` { | } ~ .

Gültige Werte:

-   0 – ermöglicht die Verwendung von Sonderzeichen in PIN-NUMMER.
-   1 – erfordert die Verwendung von mindestens Sonderzeichen im PIN.
-   2 - die Verwendung von Sonderzeichen in PIN-NUMMER lässt nicht zu werden.

Standardwert ist 2. Standardverhalten der PIN Komplexität ist die Ziffern erforderlich sind, und alle anderen Zeichensätzen sind nicht zulässig. Alle Zeichensätze sind zulässig, jedoch keine explizit erforderlich sind, wird das Standardverhalten des PIN Komplexität angewendet.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und Ersetzen Sie.

<a href="" id="tenantid-policies-pincomplexity-digits"></a>***TenantId*/Policies/PINComplexity/Digits**  
Ganze Zahl, die die Verwendung von Ziffern in der Windows Hello für Business PIN konfiguriert.

Gültige Werte:

-   0 – ermöglicht die Verwendung von Ziffern in PIN-NUMMER.
-   1 – erfordert die Verwendung von mindestens eine Ziffer in PIN-NUMMER.
-   2 - lässt nicht die Verwendung von Ziffern in PIN.

Standardwert ist 1. Standardverhalten für PIN Komplexität ist mit Ziffern erforderlich sind und alle anderen Zeichensätzen sind nicht zulässig. Alle Zeichensätze sind zulässig, jedoch keine explizit erforderlich sind, wird das Standardverhalten des PIN Komplexität angewendet.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen und ersetzen.

<a href="" id="tenantid-policies-pincomplexity-history"></a>***TenantId*/Policies/PINComplexity/History**  
Integer-Wert, der die Anzahl der vergangenen PINs angibt, die auf ein Benutzerkonto verknüpft werden können, die nicht wiederverwendet werden kann. Die größte Zahl, die Sie für diese Einstellung konfigurieren können, beträgt 50. Die kleinste Zahl für diese Einstellung konfigurierbaren ist 0. Wenn diese Richtlinie auf 0 festgelegt ist, ist die Speicherung von vorherigen PINs nicht erforderlich. Dieser Knoten wurde in Windows 10, Version 1511 hinzugefügt.

In der Gruppe von PINs das Benutzerkonto zugeordnet ist die aktuelle PIN des Benutzers enthalten. PIN-Verlauf wird nicht beibehalten, über eine PIN zurücksetzen.

Standardwert ist 0.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen und ersetzen.

<a href="" id="tenantid-policies-pincomplexity-expiration"></a>***TenantId*/Policies/PINComplexity/Expiration**  
Integer-Wert gibt die Zeitspanne (in Tagen) an, die eine PIN werden können verwendet werden, bevor das System den Benutzer es ändern müssen. Die größte Zahl für diese Einstellung konfigurierbaren ist 730. Die kleinste Zahl für diese Einstellung konfigurierbaren ist 0. Wenn diese Richtlinie auf 0 festgelegt ist, wird der Benutzer PIN nie ablaufen. Dieser Knoten wurde in Windows 10, Version 1511 hinzugefügt.

Standardwert ist 0.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

<a href="" id="tenantid-policies-remote--only-for---device-vendor-msft-"></a>** *TenantId*/Policies/Remote** (nur für ./Device/Vendor/MSFT)  
Interior-Knoten zum Definieren von remote Windows Hello für Geschäftsrichtlinien. Dieser Knoten wurde in Windows 10, Version 1511 hinzugefügt.

<a href="" id="tenantid-policies-remote-useremotepassport--only-for---device-vendor-msft-"></a>** *TenantId*/Policies/Remote/UseRemotePassport** (nur für ./Device/Vendor/MSFT)  
Boolescher Wert zum Aktivieren oder Deaktivieren der Verwendung von remote Windows Hello für Unternehmen verwendet. Remote Windows Hello für Unternehmen bietet die Möglichkeit, bei einem tragbaren, registrierte Gerät als Companion Gerät zum desktop Authentifizierung verwendet werden. Remote Windows Hello für Business vorausgesetzt, dass der Desktop Azure AD verbunden und, dass das Gerät Companion ein Windows Hello für Business PIN verfügt. Dieser Knoten wurde in Windows 10, Version 1511 hinzugefügt.

Standardwert ist false. Wenn Sie diese Richtlinie auf "true" gesetzt, Remote Windows Hello für Unternehmen ist aktiviert, und ein portable, registrierte Gerät als Companion Gerät für desktop-Authentifizierung verwendet werden kann. Wenn Sie diese Richtlinie auf False festlegen, wird Remote Windows Hello für Unternehmen deaktiviert.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

<a href="" id="usebiometrics"></a>**UseBiometrics**  
Dieser Knoten ist veraltet. Verwenden Sie stattdessen **Biometrik/UseBiometrics** Knoten.

<a href="" id="biometrics--only-for---device-vendor-msft-"></a>**Biometrie** (nur für ./Device/Vendor/MSFT)  
Knoten zum Definieren von biometrischer Einstellungen. Dieser Knoten wurde in Windows 10, Version 1511 hinzugefügt.

<a href="" id="biometrics-usebiometrics--only-for---device-vendor-msft-"></a>**Biometrik/UseBiometrics** (nur für ./Device/Vendor/MSFT)  
Boolescher Wert zum Aktivieren oder Deaktivieren der Verwendung von biometrische Gesten verwendet wird, wie-Bewegung Oberfläche und Fingerabdruck, anstatt die PIN für Windows Hello für Unternehmen. Müssen die Benutzer weiterhin eine PIN konfigurieren sie konfigurieren biometrische Gesten bei Fehlern verwenden. Dieser Knoten wurde in Windows 10, Version 1511 hinzugefügt.

Standardwert ist true. Wenn Sie diese Richtlinie auf "true" festlegen, werden biometrische Gesten für die Verwendung mit Windows Hello für Unternehmen aktiviert. Wenn Sie diese Richtlinie auf False festgelegt, werden biometrische Gesten für die Verwendung mit Windows Hello für Business deaktiviert.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

<a href="" id="biometrics-facialfeaturesuseenhancedantispoofing--only-for---device-vendor-msft-"></a>**Biometrik/FacialFeaturesUseEnhancedAntiSpoofing** (nur für ./Device/Vendor/MSFT)  
Boolescher Wert zum Aktivieren oder Deaktivieren von erweiterten Anti-spoofing für die Erkennung von Gesichtsausdruck Funktion auf Geräten, die sie unterstützen. Dieser Knoten wurde in Windows 10, Version 1511 hinzugefügt.

Wenn diese Richtlinie nicht konfiguriert ist, kann der Benutzer wählen, ob Anti-spoofing aktiviert oder deaktiviert werden soll. Wenn Sie diese Richtlinie auf "true" festlegen, wird erweiterte Anti-spoofing auf Geräten erforderlich, die dies unterstützen. Wenn Sie diese Richtlinie auf False festlegen, erweiterte Anti-spoofing ist deaktiviert, und der Benutzer kann nicht auf aktivieren.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

## <a name="examples"></a>Beispiele


Es folgt ein Beispiel zum Festlegen von Windows Hello für Unternehmen und Festlegen von PIN-Richtlinien. Es wird auch für die Verwendung von Biometrik und TPM.

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
          <SyncBody>
            <Add>
              <CmdID>2</CmdID>
              <Item>
                <Target>
                  <LocURI>
                    ./Vendor/MSFT/PassportForWork/5NEMDU42-45CC-8CBL-8BPF-D7092646325F
                  </LocURI>
                </Target>
              </Item>
            </Add>
            <Add>
              <CmdID>3</CmdID>
              <Item>
                <Target>
                  <LocURI>
                    ./Vendor/MSFT/PassportForWork/5NEMDU42-45CC-8CBL-8BPF-D7092646325F/Policies/UsePassportForWork
                  </LocURI>
                </Target>
                <Meta>
                  <Format xmlns="syncml:metinf">bool</Format>
                  <Type>text/plain</Type>
                </Meta>
                <Data>true</Data>
              </Item>
            </Add>
            <Add>
              <CmdID>4</CmdID>
              <Item>
                <Target>
                  <LocURI>
                    ./Vendor/MSFT/PassportForWork/5NEMDU42-45CC-8CBL-8BPF-D7092646325F/Policies/RequireSecurityDevice
                  </LocURI>
                </Target>
                <Meta>
                  <Format xmlns="syncml:metinf">bool</Format>
                  <Type>text/plain</Type>
                </Meta>
                <Data>true</Data>
              </Item>
            </Add>
            <Add>
              <CmdID>5</CmdID>
              <Item>
                <Target>
                  <LocURI>
                    ./Vendor/MSFT/PassportForWork/5NEMDU42-45CC-8CBL-8BPF-D7092646325F/Policies/PINComplexity/MinimumPINLength
                  </LocURI>
                </Target>
                <Meta>
                  <Format xmlns="syncml:metinf">int</Format>
                  <Type>text/plain</Type>
                </Meta>
                <Data>8</Data>
              </Item>
            </Add>
            <Add>
              <CmdID>6</CmdID>
              <Item>
                <Target>
                  <LocURI>
                    ./Vendor/MSFT/PassportForWork/5NEMDU42-45CC-8CBL-8BPF-D7092646325F/Policies/PINComplexity/MaximumPINLength
                  </LocURI>
                </Target>
                <Meta>
                  <Format xmlns="syncml:metinf">int</Format>
                  <Type>text/plain</Type>
                </Meta>
                <Data>16</Data>
              </Item>
            </Add>
            <Add>
              <CmdID>7</CmdID>
              <Item>
                <Target>
                  <LocURI>
                    ./Vendor/MSFT/PassportForWork/5NEMDU42-45CC-8CBL-8BPF-D7092646325F/Policies/PINComplexity/UppercaseLetters
                  </LocURI>
                </Target>
                <Meta>
                  <Format xmlns="syncml:metinf">int</Format>
                  <Type>text/plain</Type>
                </Meta>
                <Data>0</Data>
              </Item>
            </Add>
            <Add>
              <CmdID>8</CmdID>
              <Item>
                <Target>
                  <LocURI>
                    ./Vendor/MSFT/PassportForWork/5NEMDU42-45CC-8CBL-8BPF-D7092646325F/Policies/PINComplexity/LowercaseLetters
                  </LocURI>
                </Target>
                <Meta>
                  <Format xmlns="syncml:metinf">int</Format>
                  <Type>text/plain</Type>
                </Meta>
                <Data>1</Data>
              </Item>
            </Add>
            <Add>
              <CmdID>9</CmdID>
              <Item>
                <Target>
                  <LocURI>
                    ./Vendor/MSFT/PassportForWork/5NEMDU42-45CC-8CBL-8BPF-D7092646325F/Policies/PINComplexity/SpecialCharacters
                  </LocURI>
                </Target>
                <Meta>
                  <Format xmlns="syncml:metinf">int</Format>
                  <Type>text/plain</Type>
                </Meta>
                <Data>2</Data>
              </Item>
            </Add>
            <Add>
              <CmdID>10</CmdID>
              <Item>
                <Target>
                  <LocURI>
                    ./Vendor/MSFT/PassportForWork/5NEMDU42-45CC-8CBL-8BPF-D7092646325F/Policies/PINComplexity/Digits
                  </LocURI>
                </Target>
                <Meta>
                  <Format xmlns="syncml:metinf">int</Format>
                  <Type>text/plain</Type>
                </Meta>
                <Data>1</Data>
              </Item>
            </Add>
            <Add>
              <CmdID>11</CmdID>
              <Item>
                <Target>
                  <LocURI>
                    ./Vendor/MSFT/PassportForWork/5NEMDU42-45CC-8CBL-8BPF-D7092646325F/Policies/PINComplexity/History
                  </LocURI>
                </Target>
                <Meta>
                  <Format xmlns="syncml:metinf">int</Format>
                  <Type>text/plain</Type>
                </Meta>
                <Data>20</Data>
              </Item>
            </Add>
            <Add>
              <CmdID>12</CmdID>
              <Item>
                <Target>
                  <LocURI>
                    ./Vendor/MSFT/PassportForWork/5NEMDU42-45CC-8CBL-8BPF-D7092646325F/Policies/PINComplexity/Expiration
                  </LocURI>
                </Target>
                <Meta>
                  <Format xmlns="syncml:metinf">int</Format>
                  <Type>text/plain</Type>
                </Meta>
                <Data>70</Data>
              </Item>
            </Add>
            <Add>
              <CmdID>13</CmdID>
              <Item>
                <Target>
                  <LocURI>
                    ./Vendor/MSFT/PassportForWork/5NEMDU42-45CC-8CBL-8BPF-D7092646325F/Policies/Remote/UseRemotePassport
                  </LocURI>
                </Target>
                <Meta>
                  <Format xmlns="syncml:metinf">bool</Format>
                  <Type>text/plain</Type>
                </Meta>
                <Data>true</Data>
              </Item>
            </Add>
            <Add>
              <CmdID>14</CmdID>
              <Item>
                <Target>
                  <LocURI>
                    ./Vendor/MSFT/PassportForWork/Biometrics/UseBiometrics
                  </LocURI>
                </Target>
                <Meta>
                  <Format xmlns="syncml:metinf">bool</Format>
                  <Type>text/plain</Type>
                </Meta>
                <Data>true</Data>
              </Item>
            </Add>
    <Add>
              <CmdID>15</CmdID>
              <Item>
                <Target>
                  <LocURI>
                    ./Vendor/MSFT/PassportForWork/Biometrics/FacialFeatureUseEnhancedAntiSpoofing
                  </LocURI>
                </Target>
                <Meta>
                  <Format xmlns="syncml:metinf">bool</Format>
                  <Type>text/plain</Type>
                </Meta>
                <Data>true</Data>
              </Item>
            </Add>
            <Final/> 
          </SyncBody>
        </SyncML>
```

 

 






