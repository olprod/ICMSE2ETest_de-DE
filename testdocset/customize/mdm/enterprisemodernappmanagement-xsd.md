---
title: XSD-EnterpriseModernAppManagement
description: "Hier wird die XSD für die Anwendungsparameter."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: D393D094-25E5-4E66-A60F-B59CC312BF57
ms.openlocfilehash: 61fb43d4d599cf973d0136914734ffb25bd0c7c6
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enterprisemodernappmanagement-xsd"></a>XSD-EnterpriseModernAppManagement


Hier wird die XSD für die Parameter der Anwendung.

``` syntax
<?xml version="1.0" encoding="utf-16"?>
<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <xs:element name="Data">
        <xs:complexType>
            <xs:sequence>
                <xs:element maxOccurs="1" name="Application">
                    <xs:complexType mixed="true">
                        <xs:sequence minOccurs="0">
                            <xs:element name="Dependencies">
                                <xs:complexType>
                                    <xs:sequence>
                                        <xs:element maxOccurs="unbounded" name="Dependency">
                                            <xs:complexType>
                                                <xs:attribute name="PackageUri" type="xs:string" use="required" />
                                            </xs:complexType>
                                        </xs:element>
                                    </xs:sequence>
                                </xs:complexType>
                            </xs:element>
                        </xs:sequence>
                        <xs:attribute name="DeploymentOptions" type="xs:unsignedByte" use="optional" />
                        <xs:attribute name="PackageUri" type="xs:string" use="required" />
                    </xs:complexType>
                </xs:element>
            </xs:sequence>
        </xs:complexType>
    </xs:element>
</xs:schema>
```

 

 






