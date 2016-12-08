---
title: AssignedAccess CSP
description: "Im AssignedAccess Konfiguration-Dienstanbieter (CSP) wird verwendet, setzen Sie das Gerät im Kioskmodus ausgeführt."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 421CC07D-6000-48D9-B6A3-C638AAF83984
ms.openlocfilehash: b60d21ce89115ccec87de0a8ce5e36f9e7f1c0f3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="assignedaccess-csp"></a>AssignedAccess CSP


Der AssignedAccess Konfiguration-Dienstanbieter (CSP) wird verwendet, setzen Sie das Gerät im Kioskmodus ausgeführt. Nachdem der CSP ausgeführt wurde, wird weiter Benutzername, der die Kioskmodus zugeordnet ist das Gerät im Kioskmodus in der Konfiguration der Kryptografiedienstanbieter angegebene Anwendung ausgeführt wird.

Schrittweise Anleitung für das Einrichten eines Geräts im Kioskmodus ausgeführt wird, finden Sie unter [Richten Sie einen Kiosk auf Windows 10 Pro, Enterprise oder Education.](http://go.microsoft.com/fwlink/p/?LinkID=722211)

> **Hinweis**  AssignedAccess CSP ist nur in Windows 10 Enterprise und Windows 10 Education unterstützt.

 

Das folgende Diagramm zeigt den AssignedAccess Konfiguration-Dienstanbieter in Baumstruktur

![Assignedaccess Csp Diagramm](images/provisioning-csp-assignedaccess.png)

<a href="" id="--vendor-msft-assignedaccess"></a>**./Vendor/MSFT/AssignedAccess**  
Stammknoten für den CSP.

<a href="" id="assignedaccess-kioskmodeapp"></a>**AssignedAccess/KioskModeApp**  
Ein JSON-Zeichenfolge, die den Namen des Benutzerkontos und Anwendung Benutzer Modell-ID (AUMID) der Kiosk-Modus app enthält. Weitere Informationen dazu, wie Sie die AUMID erhalten möchten befolgen Sie die Informationen in [dieser Microsoft-Website](http://go.microsoft.com/fwlink/p/?LinkId=404220).

In Windows 10 1607 Version, können Sie eine bereitgestellte app so konfigurieren Sie den Kioskmodus zurückgekehrt. Weitere Informationen dazu, wie Sie eine app Remote bereitgestellt werden finden Sie unter [Enterprise-app-Verwaltung](enterprise-app-management.md).

Es folgt ein Beispiel:

``` syntax
{"Account":"redmond\\kioskuser","AUMID":"Microsoft.Windows.Contoso_cw5n1h2txyewy!Microsoft.ContosoApp.ContosoApp"}
```

Beim Konfigurieren der app Kiosk-Modus wird der Kontonamen, den Zielbenutzer erhalten verwendet werden. Der Name des Dienstkontos umfasst Domänen- und Benutzernamen ein.

> **Hinweis**  Der Domänenname kann optional sein, wenn das System der Benutzernamen eindeutig ist.

 

Für ein lokales Konto sollte der Domänenname den Namen des Geräts. Wenn Get auf diesem Knoten ausgeführt wird, wird der Domänenname immer in der Ausgabe zurückgegeben.

Die unterstützten Vorgänge sind hinzufügen, löschen, Get und ersetzen. Wenn keine Konfiguration vorhanden ist, fehl, die Methoden Get und löschen. Wenn bereits eine Konfiguration für Kiosk-Modus app vorhanden ist, schlägt die Add-Methode. Das Datenmuster für hinzufügen und Ersetzen ist identisch.

## <a name="examples"></a>Beispiele


KioskModeApp hinzufügen

``` syntax
<SyncML xmlns='SYNCML:SYNCML1.2'>
   <SyncBody>
       <Add>
           <CmdID>2</CmdID>
           <Item>
               <Target>
                   <LocURI>./Device/Vendor/MSFT/AssignedAccess/KioskModeApp</LocURI>
               </Target>
               <Meta>  
                   <Format xmlns="syncml:metinf">chr</Format>  
               </Meta>  
               <Data>{"Account":"Domain\\AccountName","AUMID":"Microsoft.WindowsCalculator_8wekyb3d8bbwe!App"}</Data>
           </Item>
       </Add>
       <Final />
   </SyncBody>
</SyncML>
```

KioskModeApp löschen

``` syntax
<SyncML xmlns='SYNCML:SYNCML1.2'>
   <SyncBody>
       <Delete>
           <CmdID>2</CmdID>
           <Item>
               <Target>
                   <LocURI>./Device/Vendor/MSFT/AssignedAccess/KioskModeApp</LocURI>
               </Target>
           </Item>
       </Delete>
       <Final />
   </SyncBody>
</SyncML>
```

KioskModeApp Get

``` syntax
<SyncML xmlns='SYNCML:SYNCML1.2'>
   <SyncBody>
       <Get>
           <CmdID>2</CmdID>
           <Item>
               <Target>
                   <LocURI>./Device/Vendor/MSFT/AssignedAccess/KioskModeApp</LocURI>
               </Target>
           </Item>
       </Get>
       <Final />
   </SyncBody>
</SyncML>
```

KioskModeApp ersetzen

``` syntax
<SyncML xmlns='SYNCML:SYNCML1.2'>
   <SyncBody>
       <Replace>
           <CmdID>2</CmdID>
           <Item>
               <Target>
                   <LocURI>./Device/Vendor/MSFT/AssignedAccess/KioskModeApp</LocURI>
               </Target>
               <Meta>  
                   <Format xmlns="syncml:metinf">chr</Format>  
               </Meta>  
               <Data>{"Account":"Domain\\AccountName","AUMID":"Microsoft.WindowsAlarms_8wekyb3d8bbwe!App"}</Data>
           </Item>
       </Replace>
       <Final />
   </SyncBody>
</SyncML>
```

 

 





