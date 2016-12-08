---
title: RemoteFind CSP
description: "Der Dienstanbieter für RemoteFind Konfiguration Ruft die Standortinformationen für ein bestimmtes Gerät."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2EB02824-65BF-4B40-A338-672D219AF5A0
ms.openlocfilehash: ac1272b1d1bf021a3726bb64d128aa904531c561
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="remotefind-csp"></a>RemoteFind CSP


RemoteFind Konfiguration Dienstanbieters werden die Standortinformationen für ein bestimmtes Gerät abgerufen.

Im folgenden Diagramm wird das RemoteFind Konfiguration Service Provider-Management-Objekt im Strukturformat von OMA-Clientbereitstellung verwendet.

![Remotefind csp](images/provisioning-csp-remotefind.png)

<a href="" id="desiredaccuracy"></a>**DesiredAccuracy**  
Optional Der Knoten akzeptiert den angeforderten RADIUS-Wert in Meter fest. Gültige Werte für die Genauigkeit werden einen beliebigen Wert zwischen 1 und 1000 Meter fest.

Der Standardwert ist 50. Ersetzen diesen Wert ersetzt nur für die aktuelle Sitzung. Der Wert wird nicht beibehalten.

Unterstützte Vorgänge sind ersetzen und Get. Der Befehl hinzufügen, wird nicht unterstützt.

<a href="" id="timeout"></a>**Timeout**  
Optional Wert ist ein DWORD-WERT in Sekunden an.

Der Standardwert ist 7, und der Bereich liegt zwischen 0 und 1800 Sekunden. Ersetzen diesen Wert ersetzt nur für die aktuelle Sitzung. Der Wert wird nicht beibehalten.

Unterstützte Vorgänge sind ersetzen und Get. Der Befehl hinzufügen, wird nicht unterstützt.

<a href="" id="maximumage"></a>**MaximumAge**  
Optional Der Wert stellt das gewünschte Zeitfenster in Minuten an, die der Server eine erfolgreiche Speicherort abrufen akzeptiert wird. Der Knoten ermöglicht es dem Server, den angeforderten Alter Wert in 100 Nanosekunden festzulegen. Gültige Werte für die Genauigkeit enthalten einen beliebigen ganzzahligen Wert zwischen 0 und 1440 Minuten.

Der Standardwert ist 60. Ersetzen diesen Wert ersetzt nur für die aktuelle Sitzung. Der Wert wird nicht beibehalten.

Unterstützte Vorgänge sind ersetzen und abrufen. Der Befehl hinzufügen, wird nicht unterstützt.

<a href="" id="location"></a>**Speicherort**  
Erforderlich. Knoten unter diesem Pfad müssen, um erfolgreich ausgeführt werden, automatisch abgefragt werden. Dies ist um zu verhindern, dass Server unvollständige Datenmengen Abfragen.

<a href="" id="latitude"></a>**Breitengrad**  
Erforderlich. Die Breite der letzten erfolgreichen remote Suche enthält.

Der zurückgegebene Wert ist double.

Der Standardwert ist Null.

Unterstützte Vorgang ist Get.

<a href="" id="longitude"></a>**Längengrad**  
Erforderlich. Die Länge der letzten erfolgreichen remote Suche enthält.

Der zurückgegebene Wert ist double.

Der Standardwert ist Null.

Unterstützte Vorgang ist Get.

<a href="" id="altitude"></a>**Höhe**  
Erforderlich. Enthält die Höhe des letzten erfolgreichen remote suchen.

Der zurückgegebene Wert ist double.

Der Standardwert ist Null.

Unterstützte Vorgang ist Get.

<a href="" id="accuracy"></a>**Genauigkeit**  
Erforderlich. Enthält die Genauigkeit der Meter mit dem Fix Speicherort, der die letzte erfolgreiche Remote suchen. Die Werte reichen von 0 bis 1000 Meter fest.

Der zurückgegebene Wert ist eine ganze Zahl.

Der Standardwert ist 0.

Unterstützte Vorgang ist Get.

<a href="" id="altitudeaccuracy"></a>**AltitudeAccuracy**  
Erforderlich. Enthält die Genauigkeit der Höhe in Meter mit dem Fix Speicherort, der die letzte erfolgreiche Remote suchen. Die Werte reichen von 0 bis 1000 Meter fest.

Der zurückgegebene Wert ist eine ganze Zahl.

Der Standardwert ist 0.

Unterstützte Vorgang ist Get.

<a href="" id="age"></a>**ALTER**  
Erforderlich. Das Alter in 100 Nanosekunden für den aktuellen Speicherort Daten enthält.

Der zurückgegebene Wert ist eine ganze Zahl.

Der Standardwert ist 0.

Unterstützte Vorgang ist Get.

## <a name="examples"></a>Beispiele


``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Atomic>  
            <CmdID>1</CmdID>  
            <Sequence> 
                <CmdID>10</CmdID>  
                <Get>         
                    <CmdID>30</CmdID>  
                    <Item>  
                        <Target>  
                            <LocURI>./Vendor/MSFT/RemoteFind/Location/Latitude</LocURI>  
                        </Target>  
                    </Item>  
                </Get> 
                <Get> 
                    <CmdID>40</CmdID>  
                    <Item>  
                        <Target>  
                            <LocURI>./Vendor/MSFT/RemoteFind/Location/Longitude</LocURI>  
                        </Target>  
                    </Item>  
                </Get> 
                <Get> 
                    <CmdID>40</CmdID>  
                    <Item>  
                        <Target>  
                            <LocURI>./Vendor/MSFT/RemoteFind/Location/Altitude</LocURI>  
                        </Target>  
                    </Item>  
                </Get> 
                <Get> 
                    <CmdID>45</CmdID>  
                    <Item>  
                        <Target>  
                            <LocURI>./Vendor/MSFT/RemoteFind/Location/Accuracy</LocURI>  
                        </Target>  
                    </Item>  
                </Get> 
                <Get> 
                    <CmdID>50</CmdID>  
                    <Item>  
                        <Target>  
                            <LocURI>./Vendor/MSFT/RemoteFind/Location/AltitudeAccuracy</LocURI>  
                        </Target>  
                    </Item>  
                </Get> 
                <Get> 
                    <CmdID>60</CmdID>  
                    <Item>  
                        <Target>  
                            <LocURI>./Vendor/MSFT/RemoteFind/Location/Age</LocURI>  
                        </Target>  
                    </Item>  
                </Get>                  
            </Sequence> 
        </Atomic> 
    </SyncBody>
</SyncML>
```

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






