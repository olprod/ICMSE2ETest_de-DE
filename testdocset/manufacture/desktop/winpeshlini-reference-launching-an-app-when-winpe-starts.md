---
author: Justinha
Description: 'Winpeshl.ini Referenz: Starten einer app beim Start von Windows PE'
ms.assetid: 107a3c05-791a-4daf-b188-b28dac96ef74
MSHAttr: PreferredLib:/library/windows/hardware
title: 'Winpeshl.ini Referenz: Starten einer app beim Start von Windows PE'
ms.openlocfilehash: 4d78819285ad43c36ff8c7ad86cd2df842782a22
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpeshlini-reference-launching-an-app-when-winpe-starts"></a>Winpeshl.ini Referenz: Starten einer app beim Start von Windows PE


Verwenden Sie die **Winpeshl.ini** -Datei in Windows Vorinstallation Environment (Windows PE) der Standard-Eingabeaufforderung mit einer Shell-Anwendung oder andere app ersetzen. Ihre app Shell kann beispielsweise eine GUI für Bereitstellung Ingenieure wählen Sie eine Methode zum Installieren von Windows bereitstellen.

Um eine benutzerdefinierte app hinzuzufügen, erstellen Sie eine Datei namens Winpeshl.ini und in %SystemRoot%\\System32 ein benutzerdefiniertes Windows PE-Abbild. Weitere Informationen finden Sie unter [Windows PE: Bereitstellen und Anpassen von](winpe-mount-and-customize.md).

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>Beispiel


``` syntax
[LaunchApp]
AppPath = %SYSTEMDRIVE%\Fabrikam\shell.exe
[LaunchApps]
%SYSTEMDRIVE%\Fabrikam\app1.exe
%SYSTEMDRIVE%\Fabrikam\app2.exe, /s "C:\Program Files\App3"
```

Die Datei Wpeshl.ini enthält möglicherweise einen oder beide der in den Abschnitten: \[LaunchApp\] und \[LaunchApps\]. Die aufgeführte apps \[LaunchApp\] und \[LaunchApps\] werden in der Reihenfolge ihres Auftretens ausgeführt und nicht starten, bis die vorherige app beendet wurde.

## <a name="span-idlaunchappspanspan-idlaunchappspanspan-idlaunchappspanlaunchapp"></a><span id="LaunchApp"></span><span id="launchapp"></span><span id="LAUNCHAPP"></span>LaunchApp


Legen Sie den `AppPath` Eintrag auf den Pfad Ihrer app. Können Sie einen vollqualifizierten Pfad, oder Sie können Umgebungsvariablen, wie `%SYSTEMDRIVE%` um den Pfad zu beschreiben.

**Hinweis**  
-   Die \[LaunchApp\] Eintrag darf nur eine app enthalten.

-   Sie können keinen Befehl angeben, der größer als 250 Zeichen ist.

-   Sie können nicht muss alle Befehlszeilenoptionen mit LaunchApp.

 

## <a name="span-idlaunchappsspanspan-idlaunchappsspanspan-idlaunchappsspanlaunchapps"></a><span id="LaunchApps"></span><span id="launchapps"></span><span id="LAUNCHAPPS"></span>LaunchApps


Verwendung der `[LaunchApps]` Abschnitt aus, um apps mit Befehlszeilenoptionen ausgeführt werden.

**Hinweis**  
-   LaunchApps ausgeführten apps unterstützt, aber häufig verwendete Befehle Skripting wird nicht unterstützt. Um Befehle auszuführen, fügen Sie ein Startskript stattdessen (startnet.cmd). Weitere Informationen finden Sie unter [Windows PE: Bereitstellen und Anpassen von](winpe-mount-and-customize.md).

-   Sie können keinen Befehl angeben, der größer als 250 Zeichen ist.

-   Command-Line Options zu einer app hinzufügen: Fügen Sie ein Komma (,) nach dem Namen der app:`%SYSTEMDRIVE%\Fabrikam\app2.exe,  <option>`

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Windows PE für Windows 10](winpe-intro.md)

[Windows PE: Debuggen von Apps](winpe-debug-apps.md)

 

 






