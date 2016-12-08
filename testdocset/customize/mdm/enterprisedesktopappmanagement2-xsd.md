---
title: XSD-EnterpriseDesktopAppManagement
description: "Dieses Thema enthält die XSD-Schemadatei für das EnterpriseDesktopAppManagement Konfiguration des Dienstanbieters DownloadInstall-Parameter."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 60980257-4F48-4A68-8E8E-1EF0A3F090E2
ms.openlocfilehash: 3a1dfad4437d61f3a73dfe0dcd3e272c6fefa822
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enterprisedesktopappmanagement-xsd"></a>XSD-EnterpriseDesktopAppManagement


Dieses Thema enthält die XSD-Schemadatei für die EnterpriseDesktopAppManagement Konfiguration des Dienstanbieters DownloadInstall-Parameter.

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Data">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="MsiInstallJob">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="Product">
                <xs:complexType>
                  <xs:sequence>
                    <xs:element name="Download">
                      <xs:complexType>
                        <xs:sequence>
                          <xs:element name="ContentURLList">
                            <xs:complexType>
                              <xs:sequence>
                                <xs:element maxOccurs="unbounded" name="ContentURL" type="xs:string" />
                              </xs:sequence>
                            </xs:complexType>
                          </xs:element>
                        </xs:sequence>
                      </xs:complexType>
                    </xs:element>
                    <xs:element name="Validation">
                      <xs:complexType>
                        <xs:sequence>
                          <xs:element name="FileHash" type="xs:string" />
                        </xs:sequence>
                      </xs:complexType>
                    </xs:element>
                    <xs:element name="Enforcement">
                      <xs:complexType>
                        <xs:sequence>
                          <xs:element name="CommandLine" type="xs:string" />
                          <xs:element name="TimeOut" type="xs:unsignedByte" />
                          <xs:element name="RetryCount" type="xs:unsignedByte" />
                          <xs:element name="RetryInterval" type="xs:unsignedByte" />
                        </xs:sequence>
                      </xs:complexType>
                    </xs:element>
                  </xs:sequence>
                  <xs:attribute name="Version" type="xs:string" use="required" />
                </xs:complexType>
              </xs:element>
            </xs:sequence>
            <xs:attribute name="id" type="xs:string" use="required" />
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

In der folgenden Tabelle werden die verschiedenen Elemente und Attribute des XSD-Datei beschrieben:

 

| Name           | Beschreibung                                                                                                                                                                        |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| MsiInstallJob  | Stammelement                                                                                                                                                                       |
| id             | Der Anwendungsbezeichner für die Anwendung installiert wird.                                                                                                                    |
| Produkt        | Untergeordnetes Element des MsiInstallJob                                                                                                                                                     |
| Version        | Zeichenfolgendarstellung der Version der Anwendung                                                                                                                                   |
| Download       | Untergeordnetes Element des Produkts. Container für Download Konfigurationsinformationen.                                                                                                        |
| ContentURLList | Untergeordnetes Element des Downloads. Liste der mindestens einen Herunterladen von Bildern URL Locator in Form von ContentURL Elemente enthält.                                                          |
| ContentURL     | Speicherort Inhalt sollte hier heruntergeladen werden. Muss, dass eine Eigenschaft URL formatiert, die auf die MSI-Datei verweist.                                                                     |
| Überprüfung     | Enthält Informationen zum Überprüfen von Content-Authentifizierung verwendet.                                                                                                                        |
| FileHash       | SHA256-Hash-Wert der Inhalt der Datei.                                                                                                                                                 |
| Erzwingung    | Beim Installieren dieser MSI-DATEI zu verwendende Eigenschaften für die Softwareinstallation                                                                                                                        |
| CommandLine    | Beim Aufrufen von MSIEXEC.exe zu verwendende Befehlszeilenoptionen                                                                                                                           |
| Timeout        | Zeitdauer in Minuten an, denen der Installationsvorgang werden, bevor Sie das Installationsprogramm ausgeführt kann berücksichtigt die Installation möglicherweise ist ein Fehler aufgetreten, und der Installationsvorgang nicht mehr überwacht. |
| RetryCount     | Häufigkeit des Vorgangs herunter, und Installation vor der Installation wird wiederholt wird als fehlgeschlagen markiert.                                                          |
| RetryInterval  | Die Zeitdauer in Minuten zwischen Retry Vorgänge.                                                                                                                                |

 

 

 






