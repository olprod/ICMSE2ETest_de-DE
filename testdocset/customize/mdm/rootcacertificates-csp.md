---
title: RootCATrustedCertificates CSP
description: RootCATrustedCertificates CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: F2F25DEB-9DB3-40FB-BC3C-B816CE470D61
ms.openlocfilehash: 61d104d67a9fea301288edd20ab5154760c7aaeb
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="rootcatrustedcertificates-csp"></a>RootCATrustedCertificates CSP


Der Dienstanbieter für RootCATrustedCertificates Konfiguration ermöglicht das Unternehmen die Zertifikate (Root Certificate Authority, CA) festgelegt.

> **Hinweis**  Die **. /User/** Konfiguration wird nicht unterstützt für **RootCATrustedCertificates/Root/**.

 

Die folgende Abbildung zeigt den RootCATrustedCertificates Konfiguration-Dienstanbieter im Strukturformat dar.

![roocacertificate](images/provisioning-csp-rootcacertificate.png)

<a href="" id="device-or-user"></a>**Gerät oder Benutzer**  
Verwenden Sie für Device-Zertifikate **./Device/Vendor/MSFT** Pfad und für Benutzerzertifikate **./User/Vendor/MSFT** Pfad.

<a href="" id="rootcatrustedcertificates"></a>**RootCATrustedCertificates**  
Der Stammknoten für den Dienstanbieter für RootCATrustedCertificates-Konfiguration.

<a href="" id="rootcatrustedcertificates-root-"></a>**RootCATrustedCertificates/Root /**  
Definiert den Zertifikatspeicher, der in diesem Fall Stamm oder eines selbstsignierten Zertifikats enthält den Speicher des Computers an.

> **Hinweis**  Die **. /User/** Konfiguration wird nicht unterstützt für **RootCATrustedCertificates/Root/**.

 

<a href="" id="rootcatrustedcertificates-ca"></a>**RootCATrustedCertificates-Zertifizierungsstelle**  
Der Knoten für Zertifikate einer Zertifizierungsstelle.

<a href="" id="rootcatrustedcertificates-trustedpublisher"></a>**RootCATrustedCertificates/TrustedPublisher**  
Der Knoten für Zertifikate von vertrauenswürdigen Herausgebern.

<a href="" id="rootcatrustedcertificates-trustedpeople"></a>**RootCATrustedCertificates/TrustedPeople**  
Der Knoten für vertrauenswürdige Personen Zertifikate.

<a href="" id="certhash"></a>**_CertHash_**  
Definiert den SHA1-Hash für das Zertifikat. Der 20-Byte-Wert des SHA1-Zertifikathash wird als ein hexadezimaler Zeichenfolgenwert angegeben.

Die unterstützten Vorgänge sind hinzufügen, löschen, und ersetzen.

<a href="" id="-encodedcertificate"></a>**/ EncodedCertificate**  
Gibt das x. 509-Zertifikat als Base64-codierte Zeichenfolge. Der Base64-String-Wert kann keine zusätzliche Formatierung Zeichen wie etwa eingebetteten Zeilenvorschübe usw. enthalten.

Die unterstützten Vorgänge sind hinzufügen, abrufen, löschen, und Ersetzen Sie.

<a href="" id="-issuedby"></a>**/ Ein Certificate-Objekt**  
Gibt den Namen des Herausgebers Zertifikat zurück. Dies ist gleichbedeutend mit dem **Aussteller** -Element in der CERT\_INFO-Datenstruktur.

Der einzige unterstützte Vorgang ist Get.

<a href="" id="-issuedto"></a>**/ Ein Certificate-Objekt**  
Gibt den Namen des Betreffs Zertifikats zurück. Dies ist gleichbedeutend mit dem **Betreff** -Element in der CERT\_INFO-Datenstruktur.

Der einzige unterstützte Vorgang ist Get.

<a href="" id="-validfrom"></a>**/ ValidFrom**  
Gibt das Startdatum des die Gültigkeit des Zertifikats zurück. Dies ist gleichbedeutend mit dem Element **nicht vor** , in der CERT\_Datenstruktur INFO.

Der einzige unterstützte Vorgang ist Get.

<a href="" id="-validto"></a>**/ ValidTo**  
Gibt das Ablaufdatum des Zertifikats zurück. Dies ist gleichbedeutend mit dem **nicht nach** Mitglied in der CERT\_Datenstruktur INFO.

Der einzige unterstützte Vorgang ist Get.

<a href="" id="-templatename"></a>**/ TemplateName**  
Gibt den Namen der Vorlage an.

Der einzige unterstützte Vorgang ist Get.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






