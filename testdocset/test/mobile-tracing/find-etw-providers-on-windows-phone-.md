---
title: Besuchen Sie ETW-Anbieter auf Windows 10 Mobile
description: "Hier geben wir Beispiele dafür, wie Sie die ETW-Anbieter auf einem Windows 10 Mobile-Gerät zu suchen."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 918791F9-B627-4AA6-A6FC-39A0B376834B
ms.openlocfilehash: acc881246fca4566b4dee95a586de66f5ec371c4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="find-etw-providers-on-windows-10-mobile"></a>Besuchen Sie ETW Providers auf Windows 10 Mobile


Hier geben wir Beispiele dafür, wie Sie die ETW-Anbieter auf einem Windows-10-Mobile-Gerät finden. Dieser Schritt ist nur für Ingenieure nutzen.

## <a name="field-medic-appx"></a>Feld Sanitäter Appx


Suchen Sie mit den Paketen MobileOS FieldMedic.appx.

Ändern Sie den Namen des FieldMedic.appx in FieldMedic.zip.

Öffnen Sie FieldMedic.zip, und öffnen Sie den Ordner ProfileXMLs.

Öffnen Sie in den Ordner ProfileXMLs jeder Profil XML-Datei, um die GUIDs der ETW-Anbieter anzuzeigen, die auf das Profil gehören. Öffnen Sie beispielsweise FieldMedic Performance.xml.

``` syntax
<EventProvider Name="A6BF0DEB-3659-40ad-9F81-E25AF62CE3C7" …/>
<EventProvider Name="331C3B3A-2005-44C2-AC5E-77220C37D6B4" …/>
<EventProvider Name="0F67E49F-FE51-4E9F-B490-6F2948CC6027" …/>
<EventProvider Name="C514638F-7723-485B-BCFC-96565D735D4A" …/>
<EventProvider Name="5412704E-B2E1-4624-8FFD-55777B8F7373" …/>
<EventProvider Name="59819D0A-ADAF-46B2-8D7C-990BC39C7C15" …/>
<EventProvider Name="5C103042-7E75-4629-A748-BDFA67607FAC" …/>
```

## <a name="manifest-files-in-the-windows-driver-kit"></a>Manifest-Dateien im Windows-Treiberkits


Suchen Sie in der Windows-Treiberkits den Manifeste Ordner.

Beispiel: C:\\Programmdateien (x86)\\Windows Kits\\10\\-Manifeste

Öffnen Sie in den Ordner Manifeste alle Manifest (MC)-Datei, um die ETW Anbieternamens und GUID finden Sie unter. Öffnen Sie beispielsweise Microsoft-Windowsphone-mtp.mc.

``` syntax
<provider name="Microsoft-WindowsPhone-Mtp"
          guid="{13D97131-EE68-43F4-A1D0-9E762D2A4729}"
```

## <a name="xperf"></a>XPerf


Stellen Sie eine TShell-Verbindung zwischen einem Computer und dem Gerät.

Geben Sie auf dem Computer in TShell, diesen Befehl aus:

``` syntax
exec-device xperf –providers I
```

Die Ausgabe sieht etwa wie folgt:

``` syntax
…
0063715b-eeda-4007-9429-ad526f62696e             : Microsoft-Windows-Services
00a083e0-1eda-4c82-9a16-e62b1bbc0659             : Microsoft-WindowsPhone-WboExt
02292a7f-12e0-4de6-8fb0-cb93cc1126d3             : Microsoft-WindowsPhone-MMResourceRegistrar
048970b2-e55c-4d10-bbc8-2ee964b745a4             : Microsoft-WindowsMobile-SyncMLDPU-Provider
04a490d4-84c6-4920-9c22-51c80825ff2c             : Microsoft-WindowsPhone-Comms-PhoneUtil
…
```

## <a name="reg-device"></a>REG-Gerät


Geben Sie in TShell diesen Befehl aus:

``` syntax
reg-device query HKLM\Software\Microsoft\Windows\CurrentVersion\WINEVT\Publishers /s > publishers.txt
```

Die Ausgabe sieht etwa wie folgt:

``` syntax
HKEY_LOCAL_MACHINE\...\Publishers\{0063715B-EEDA-4007-9429-AD526F62696E}
    (Default)    REG_SZ    Microsoft-Windows-Services
    Enabled    REG_DWORD    0x1
    MessageFileName    REG_SZ    C:\windows\System32\services.exe
    ResourceFileName    REG_SZ    C:\windows\System32\services.exe

HKEY_LOCAL_MACHINE\...\Publishers\{00A083E0-1EDA-4c82-9A16-E62B1BBC0659}
    (Default)    REG_SZ    Microsoft-WindowsPhone-WboExt
    Enabled    REG_DWORD    0x1
    MessageFileName    REG_SZ    C:\windows\System32\WboExt.dll
    ResourceFileName    REG_SZ    C:\windows\System32\WboExt.dll
…
```

## <a name="tracelog"></a>TRACELOG


Geben Sie im TShell diese Befehle aus:

Produktion von Bildern möglicherweise Sie WinPhoneCritical und WinPhoneCircular-Sitzungen interessiert sein.

``` syntax
 Copy imageCopy code  
exec-device tracelog –q WinPhoneCritical -lp
exec-device tracelog –q WinPhoneCircular -lp
```

Die Ausgabe sieht etwa wie folgt:

``` syntax
Logger Name:            WinPhoneCritical
…
Log Mode:               AddToTriageDump  Buffering-only
…
Log Filename:

Enabled Providers:
## Guid                                  Level  Flags

531ab09a-fd58-4d14-bace-bdd7f8e910eb      2  0xffffffffffffffff
ebfe7216-281a-4601-875f-17d1cabed9e0      2  0x00000007
08dde8cc-029f-4e95-9d84-259ccf3a6808      2  0x00000007
…
21f1f21b-c2f6-47d0-bafc-5b75a86f5343      2  0x00000001
Total of 154 providers
```

 

 






