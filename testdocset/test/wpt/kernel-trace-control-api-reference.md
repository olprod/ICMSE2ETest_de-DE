---
title: Kernel Trace Steuerelement API-Referenz
description: Kernel Trace Steuerelement API-Referenz
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 16ecacd5-25aa-43d7-b842-cb8f92db8eeb
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 9c65487f0aa1ea28bdee68ebe631b17f9b3424da
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="kernel-trace-control-api-reference"></a>Kernel Trace Steuerelement API-Referenz


Diese API ermöglicht das Erfassen von Kernel-Stapel Spuren, Zusammenführen mehrerer Tracedateien für die Analyse Heap tracing und Systeminformationen in die zusammengeführten Dateien.

Aus dem Kernel Trace Steuerelement-API in Windows Vista verfügbar.

Unter Windows 7 und Windows Vista, Stackwalking auf Systeme erfordert, dass Sie den Registrierungswert **DisablePagingExecutive** in X64 **HKLM\\SYSTEM\\CurrentControlSet\\Steuerelement\\Session Manager\\Speicherverwaltung**. Weitere Informationen finden Sie unter [DisablePagingExecutive](http://go.microsoft.com/fwlink/p/?linkid=213095).

**Hinweis**  Systeme mit Windows 8 und höher ist nicht erforderlich, diese Änderung der Registrierung.

 

Im folgenden Beispiel wird veranschaulicht, wie dieser Registrierungswert abgefragt wird.

``` syntax
@REG QUERY "HKLM\System\CurrentControlSet\Control\Session Manager\Memory Management" -v DisablePagingExecutive
```

Im folgenden Beispiel wird gezeigt, wie Stackwalking zu aktivieren.

``` syntax
@REG ADD "HKLM\System\CurrentControlSet\Control\Session Manager\Memory Management" -v DisablePagingExecutive -d 0x1 -t REG_DWORD -f
@IF NOT %ERRORLEVEL% == 0 echo error: Could not configure system for 64-bit stackwalking. Please run this script from an elevated administrator console.
```

**Hinweis**  
Damit diese Änderung wirksam wird, müssen Sie das System neu starten.

 

Im folgenden Beispiel wird veranschaulicht, wie Stackwalking deaktiviert wird.

``` syntax
@REG ADD "HKLM\System\CurrentControlSet\Control\Session Manager\Memory Management" -v DisablePagingExecutive -d 0x0 -t REG_DWORD -f
@IF NOT %ERRORLEVEL% == 0 echo error: Could not remove 64-bit stackwalking configuration. Please run this script from an elevated administrator console.
```

**Hinweis**  
Damit diese Änderung wirksam wird, müssen Sie das System neu starten.

 

## <a name="in-this-section"></a>In diesem Abschnitt


[Funktionen](functions-wpa.md)

[Strukturen](structures-wpa.md)

[Ablaufverfolgungsflags-Steuerelement](trace-control-flags.md)

[Verfolgen von Steuerelement Ereignistypen](trace-control-event-types.md)

[Benutzerdefinierte Einfügung von Systeminformationen](custom-injection-of-system-information.md)

## <a name="related-topics"></a>Verwandte Themen


[Windows Performance Toolkit technische Referenz](windows-performance-toolkit-technical-reference.md)

 

 







