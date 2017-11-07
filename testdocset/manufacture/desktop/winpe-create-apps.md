---
author: Justinha
Description: 'Windows PE: Erstellen von Apps'
ms.assetid: 93848579-fd6d-4d51-bb51-f5f412833ad8
MSHAttr: PreferredLib:/library/windows/hardware
title: 'Windows PE: Erstellen von Apps'
ms.openlocfilehash: 69e2ce341fb028c481356bfb38159efa657c6e16
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-create-apps"></a>Windows PE: Erstellen von Apps


Unabhängige Softwarehersteller (ISVs) und Original Equipment Manufacturers, OEMs (OEMs) zum Erstellen der angepassten Bereitstellung und Dienstprogramme zur Wiederherstellung wird Windows PE (Windows PE) lizenziert. Dieses Thema enthält Richtlinien für ISVs und OEMs Entwicklung, Bereitstellung und Recovery-apps, die in Windows PE ausgeführt.

**Hinweis**  
Windows PE ist kein allgemeine Operating System. Es kann nicht zu anderen Zwecken als Bereitstellung und Wiederherstellung verwendet werden. Es sollte nicht als einem thin-Client oder einem eingebetteten Betriebssystem verwendet werden. Es gibt andere Produkte Microsoft® wie Windows Embedded CE, die für diese Zwecke verwendet werden können.

 

## <a name="span-idextensibilityspanspan-idextensibilityspanspan-idextensibilityspanextensibility"></a><span id="Extensibility"></span><span id="extensibility"></span><span id="EXTENSIBILITY"></span>Erweiterbarkeit


Die meisten Windows PE apps sind Shell-Funktion apps, die eigene GUI bereitstellen. Zwei Beispiele sind die Windows-Setup-app und die Windows Recovery Environment (Windows RE).

-   Wenn es zum Anzeigen einer Eingabeaufforderung akzeptabel ist, ändern Sie Startnet.cmd – Dies ist die geeignetsten Möglichkeit für den automatischen start eine app. Finden Sie unter [Windows PE: Bereitstellen und Anpassen von](winpe-mount-and-customize.md).

-   Wenn Ihre app umgehen die Befehlszeile, und starten Sie in der Benutzeroberfläche werden möchten, verwenden Sie Winpeshl.exe, Wpeinit.exe, wpeutil.exe und wpeutil.dll.

## <a name="span-idwinpeshlexewpeinitexewpeutilexeandwpeutildllspanspan-idwinpeshlexewpeinitexewpeutilexeandwpeutildllspanspan-idwinpeshlexewpeinitexewpeutilexeandwpeutildllspanwinpeshlexe-wpeinitexe-wpeutilexe-and-wpeutildll"></a><span id="Winpeshl.exe__Wpeinit.exe__wpeutil.exe__and_wpeutil.dll"></span><span id="winpeshl.exe__wpeinit.exe__wpeutil.exe__and_wpeutil.dll"></span><span id="WINPESHL.EXE__WPEINIT.EXE__WPEUTIL.EXE__AND_WPEUTIL.DLL"></span>Winpeshl.exe, Wpeinit.exe, wpeutil.exe und wpeutil.dll


Winpeshl.exe ist standardmäßig der erste Prozess ausgeführt werden, wenn Windows PE gestartet wird. Dies wird durch den folgenden Registrierungswert vom Typ REG angegeben\_SU.

``` syntax
HKEY_LOCAL_MACHINE
   System
      Setup
         CmdLine
```

Winpeshl.exe sucht nach einer Datei Winpeshl.ini aufgerufen. Wenn die Datei nicht vorhanden ist, beginnt Winpeshl.exe einen Cmd.exe Prozess, der das Skript Startnet.cmd ausgeführt wird. Wenn Winpeshl.ini vorhanden ist und es apps zum Starten enthält, werden diese apps anstelle von Cmd.exe ausgeführt.

Wpeinit.exe installiert Plug & Play (Plug & Play-) Geräte, starten den Netzwerken-Stapel und Verarbeitung Unattend.xml Einstellungen beim Start von Windows PE. Weitere Informationen finden Sie unter [Wpeinit und Startnet.cmd: Verwenden von Windows PE zum Starten des Skripts](wpeinit-and-startnetcmd-using-winpe-startup-scripts.md).

Netzwerke kann durch Ausführen von entweder durch Zulassen der Wpeinit.exe beim Start von Windows PE ausgeführt oder durch Ausführen des Befehls [Wpeutil Command-Line Options](wpeutil-command-line-options.md) können Sie jederzeit gestartet werden.

Angepasste Shell, die apps direkt in Wpeutil.dll mit den Funktionen [LoadLibrary](http://go.microsoft.com/fwlink/?LinkId=203026) und [GetProcAddress](http://go.microsoft.com/fwlink/?LinkId=203027) anrufen können. Weitere Informationen finden Sie unter [INFO: Alternativen zur Verwendung von GetProcAddress() mit LoadLibrary()](http://go.microsoft.com/fwlink/?LinkId=203028).

Jede von Wpeutil.dll exportierten Funktionen hat dieselbe Funktionssignatur als [WinMain-Funktion](http://go.microsoft.com/fwlink/?LinkId=203029), wie im folgenden Codebeispiel dargestellt.

``` syntax
int InitializeNetworkingW(
HINSTANCE hInstance,
HINSTANCE hPrevInstance,
LPSTR lpCmdLine,
int nCmdShow
);
```

Im folgenden Codebeispiel veranschaulicht das Netzwerk nicht initialisiert werden.

``` syntax
#include <windows.h>
#include <tchar.h>
#include <stdio.h>
typedef int (*WpeutilFunction)( 
HINSTANCE hInst, 
HINSTANCE hPrev, 
LPTSTR lpszCmdLine, 
int nCmdShow 
);
int __cdecl _tmain( int argc, TCHAR *argv[] )
{
    
HMODULE         hWpeutil          = NULL;
    
WpeutilFunction InitializeNetwork = NULL;
    
int             result            = 0;
    
TCHAR           szCmdLine[]       = _T("");
    
hWpeutil = LoadLibrary( _T("wpeutil") );
    
if( NULL == hWpeutil )
    
{
        _tprintf( _T("Unable to load wpeutil.dll \ n") );
        
return GetLastError();
}
    
InitializeNetwork = (WpeutilFunction)GetProcAddress( 
hWpeutil, 
"InitializeNetworkW" 
);
    
if( NULL == InitializeNetwork )
    
{
        
FreeLibrary( hWpeutil );
        
return GetLastError();
    
}
    
result = InitializeNetwork( NULL, NULL, szCmdLine, SW_SHOW );
    
if( ERROR_SUCCESS == result )
    
{
        _tprintf( _T("Network initialized. \ n") );
    
}
  
else
    
{
        _tprintf( _T("Initialize failed: 0x%08x"), result );
    
}
    
FreeLibrary( hWpeutil );

return result;}
```

Eine vollständige Liste der Wpeutil.dll exportiert finden Sie unter [Wpeutil Command-Line Options](wpeutil-command-line-options.md).

## <a name="span-idvisualstudioprojectsettingsspanspan-idvisualstudioprojectsettingsspanspan-idvisualstudioprojectsettingsspanvisual-studio-project-settings"></a><span id="Visual_Studio_project_settings"></span><span id="visual_studio_project_settings"></span><span id="VISUAL_STUDIO_PROJECT_SETTINGS"></span>Visual Studio-Projekt-Einstellungen


Einige grundlegenden Visual Studio Project-Einstellungen können von den Standardeinstellungen mithilfe der Visual Studio-Projekt-Assistenten erstellt abweichen. Stellen Sie sicher, dass Sie Ihr Projekt Buildeinstellungen eingerichtet, zum Erstellen von apps und DLLs, die mit Windows PE kompatibel sind:

1.  Sie müssen Windows PE-apps mit systemeigenem Code für C oder C++ entwickeln, die nicht MFC oder ATL verwendet Daher Wenn Sie die Visual Studio-Projekt-Assistenten verwenden, wählen Sie ein Win32-Projekt, und stellen Sie sicher, dass weder MFC noch ATL-aktiviert sind.

2.  Festlegen Sie Ihre Projektoptionen zum Verknüpfen mit den statischen C/C++-Laufzeitbibliotheken, nicht die DLL-Version von Msvcrt.dll.

3.  Öffnen Sie die Projekteigenschaften fest, und legen **Konfigurationseigenschaften \\ C/C++-Laufzeitbibliothek** zu **Multithread** oder **Multithread-Debuggen**nicht eine der DLL-Versionen. Wenn Sie diesen Schritt nicht durchführen, kann Ihre app in Windows PE nicht ausgeführt.

4.  Wenn Ihre app auf der 64-Bit-Version von Windows PE gehostet werden soll, legen Sie das Projekt Buildoptionen, um alle Binärdateien mit der X64 kompilieren Compiler in Visual Studio.

5.  Wenn Ihre app auf der 32-Bit-Version von Windows PE gehostet werden soll, legen Sie Project-Optionen, um mit der X86 kompilieren Compiler erstellt.

6.  Stellen Sie sicher, dass das Projekt nicht mit der/CLR verfügt: Compiler Option festlegen. Diese Option erzeugt verwalteten C++-Code, der nicht auf Windows PE ausgeführt werden.

**Warnung**  
Ihre app können angepasste DLL-Dateien, die Sie schreiben oder von einem Drittanbieter lizenzieren. Fügen Sie diese DLL-Dateien an Ihrer app für Windows PE. Allerdings verwenden Sie Msvcrt.dll nicht, und nehmen Sie keine zusätzliche Windows-DLL-Dateien, die nicht Teil der Windows PE sind.

 

## <a name="span-idapicompatibilityreferencespanspan-idapicompatibilityreferencespanspan-idapicompatibilityreferencespanapi-compatibility-reference"></a><span id="API_Compatibility_reference"></span><span id="api_compatibility_reference"></span><span id="API_COMPATIBILITY_REFERENCE"></span>Kompatibilität von API-Referenz


Windows PE ist eine einfache, bootstrap Betriebssystem, basierend auf eine Teilmenge der Komponenten aus dem Windows-Betriebssystem. Es dient zum Hosten von apps-Bereitstellung und Wiederherstellung. Als solche enthält viele Windows-Binärdateien, die zum Hosten der APIs, die für diese Klassen App am wichtigsten sind erforderlich sind. Aufgrund der Größe und anderen Einschränkungen Entwurf nicht von allen Windows-Binärdateien in Windows PE vorhanden sind und werden daher nicht alle Windows-APIs vorhanden oder verwendbar.

### <a name="span-idsupportedapisinwindowspespanspan-idsupportedapisinwindowspespanspan-idsupportedapisinwindowspespansupported-apis-in-windows-pe"></a><span id="Supported_APIs_in_Windows_PE"></span><span id="supported_apis_in_windows_pe"></span><span id="SUPPORTED_APIS_IN_WINDOWS_PE"></span>Unterstützte APIs in Windows PE

Die folgenden APIs sind in Windows PE unterstützt:

1.  [Windows-API-Sätze (Mincore.lib)](http://go.microsoft.com/fwlink/?LinkId=330240).

2.  [Deployment Image Servicing and Management (DISM)-API (Dismapi.lib)](http://go.microsoft.com/fwlink/?LinkId=330239).

3.  [Imaging-APIs für Windows (Wimgapi.lib)](http://go.microsoft.com/fwlink/?LinkId=330241).

Wenn eine API verhält sich wie dies der Fall auf den vollständigen Windows-Betriebssystem ist und wie in das Betriebssystem Microsoft Windows SDK für Windows dokumentiert, es berücksichtigt werden unterstützt und kann von apps verwendet werden, sofern nicht anders angegeben. Da Windows PE auf Windows-Komponenten basiert, enthält sie eine beträchtliche Teilmenge der Windows-APIs, die in das Betriebssystem Microsoft Windows SDK für Windows veröffentlicht werden. Der Parameter Konventionen und das Verhalten von dieser unterstützten APIs aufrufen werden derselben oder nahezu identisch auf vollständigen Windows-Betriebssystems, wenn sie von der eindeutigen Windows PE-Umgebung betroffen sind. Apps, die nur diese APIs sollte zwischen der vollständigen Windows-Betriebssystem und Windows PE portable sein.

In einigen Fällen wird eine Teilmenge der möglichen Parameterwerte auf Windows PE verwendbar. Dies kann aufgrund von Bedingungen für die Laufzeitumgebung, wie die Ausführung auf einem schreibgeschützten Medium, die keinen Zugriff auf permanent oder andere Design-Einschränkungen eindeutig sein. In diesem Fall die API möglicherweise nicht unterstützt, aber möglicherweise noch verwendet werden, um eine bestimmte Aufgabe auszuführen, wenn keine andere Alternative vorhanden ist.

Im Allgemeinen, wenn eine API nicht richtig funktioniert oder gar nicht auf Windows PE es wird nicht unterstützt und dürfen nicht verwendet werden, auch wenn er in einer Binärdatei befindet, die in Windows PE enthalten ist. Die API schlägt möglicherweise fehl, da Windows PE eine Teilmenge des Betriebssystems Windows oder aufgrund von der Laufzeit Entwurfsaspekte eindeutigen Windows PE ist. Solche Fehler werden Fehler in Windows PE nicht berücksichtigt.

Da viele Windows-Komponenten nicht in Windows PE vorhanden sind, sind viele APIs nicht verfügbar. Sie vollständig fehlen möglicherweise, weil die Windows-Binärdatei in der sie sich befinden, nicht vorhanden ist. Alternativ können sie nur teilweise vorhanden sein, da zwar Windows binary in der sie sich befinden vorhanden ist, eine oder mehrere Binärdateien denen sie abhängen nicht werden. Darüber hinaus einige APIs, die in Windows PE vorhanden sind nicht einwandfrei funktionsfähig sein und Verhalten sich anders als bei in Fenstern. Diese APIs werden nicht unterstützt und dürfen nicht verwendet werden, da ihr Verhalten auf Windows PE nicht definiert ist.

In einigen Fällen kann keine geeigneten API, eine bestimmte Aufgabe vorhanden sein. Wenn eine alternative Lösung suchen möchten, benötigen Sie verschiedene app Logik, anderen Algorithmus Entwurf oder Neudefinition eines das zugrunde liegende Problem.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows PE für Windows 10](winpe-intro.md)

[Windows PE: Debuggen von Apps](winpe-debug-apps.md)

 

 






