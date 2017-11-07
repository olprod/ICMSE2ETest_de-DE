---
author: kpacquer
Description: Entwickelt testanwendungen MMOS
ms.assetid: 1149e3d6-79d9-443e-9561-c030069eb79a
MSHAttr: PreferredLib:/library/windows/hardware
title: Entwickelt testanwendungen MMOS
ms.openlocfilehash: 616b2aa552d9a018b529626d8e97f1301a3da5dc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="develop-mmos-test-applications"></a>Entwickelt testanwendungen MMOS


Entwickeln von Tests in MMOS im Benutzermodus ist im Benutzermodus Anwendungsentwicklung sehr ähnlich.

## <a name="span-idtestdevelopmentinmmosspanspan-idtestdevelopmentinmmosspanspan-idtestdevelopmentinmmosspantest-development-in-mmos"></a><span id="Test_development_in_MMOS"></span><span id="test_development_in_mmos"></span><span id="TEST_DEVELOPMENT_IN_MMOS"></span>Testentwicklung in MMOS


Gehen Sie folgendermaßen vor, zu erstellen, bereitstellen und testen eine MMOS testanwendung.

1.  Erstellen einer app.

2.  Hinzufügen von Code zum Testen der gewünschten Komponente und anzeigen oder senden die Ergebnisse nach Bedarf. Beispielsweise kann diesen Beispielcode in MMOS eine Nachricht Konsole an verwendet werden.

    ``` syntax
#include <stdio.h>
#include <Windows.h>

    int main()
    {
        int i = 0;
        for(;;)
        {    
            wprintf(L"Test");
            Sleep(500);
            if (i == 12)
            {
                wprintf(L"Done");
                break;
            }
            i++;
        }
        return 0;
    }
    ```

3.  Erstellen Sie die Anwendung in Visual Studio zu testen.

4.  Suchen Sie die Binärdateien generiert, wenn Sie die app erstellt. Normalerweise werden in einem Unterverzeichnis des Ordners Projects, z. B. * \\MyProject\\Arm\\Debuggen\\*.

5.  Signieren Sie die ausführbare Datei mit dem Skript sign.cmd in der "WPDKCONTENTROOT %\\Tools\\Bin\\i386"-Ordner, wie im folgenden Beispiel dargestellt.

    ``` syntax
    sign.cmd ApplicationForDrivers.exe
    ```

6.  Um Ihre app zu testen, kopieren Sie es auf das Gerät im Laufwerk C:\\Daten\\Directory mithilfe von FTP testen und über Telnet ausführen. Weitere Informationen finden Sie unter [Bereitstellen und Testen einer Benutzermodus - testanwendung in MMOS](deploy-and-test-a-user-mode-test-application-in-mmos.md).

## <a name="span-idlibrariesinmmosspanspan-idlibrariesinmmosspanspan-idlibrariesinmmosspanlibraries-in-mmos"></a><span id="Libraries_in_MMOS"></span><span id="libraries_in_mmos"></span><span id="LIBRARIES_IN_MMOS"></span>Bibliotheken in MMOS


Hinzufügen einer Lib im MMOS ist vergleichbar mit dem Hinzufügen einer Lib in der Produktion OS. Derzeit wird dieses Lib Standardspeicherort für das Kit in Visual Studio konfiguriert.

``` syntax
$(WPDKInstallDir)lib\$(KitOs)\wp_um\$(Platform)
$(WPDKInstallDir)Tools\WPE\CRT\lib\$(Platform)
```

Wählen Sie zum Hinzufügen einer Lib in Visual Studio **Project** &gt; **Eigenschaften** &gt; **Konfigurationseigenschaften** &gt; **VC++ Verzeichnisse** &gt; **Verzeichnisse enthalten**. Für die Verwendung die MMOS-Bibliotheken fügen Sie das folgende Verzeichnis auf den Pfad an.

``` syntax
$(WPDKContentRoot)include\mmos
```

Fügen Sie das Arm-Verzeichnis. Wählen Sie in Visual Studio **Project** &gt; **Eigenschaften** &gt; **Konfigurationseigenschaften** &gt; **Linker** &gt; **Allgemeine** &gt; **Weitere Library-Verzeichnisse**. Fügen Sie die folgenden Verzeichnissen MMOS Bibliotheken für die Verwendung auf den Pfad.

``` syntax
$(WPDKContentRoot)lib\win8\mmos\arm
```

## <a name="span-idsecurityinmmosspanspan-idsecurityinmmosspanspan-idsecurityinmmosspansecurity-in-mmos"></a><span id="Security_in_MMOS"></span><span id="security_in_mmos"></span><span id="SECURITY_IN_MMOS"></span>Sicherheit in MMOS


In entwicklungsumgebungen können Benutzermodus Testbinärdateien angemeldet Test (nicht signierte Produktion) sein. Mithilfe des in [Anmelde-Binärdateien und Paketen](https://msdn.microsoft.com/library/windows/hardware/dn789217) beschriebenen Prozess der um Anmeldung die Binärdateien zu testen.

Wenn die Testbinärdateien nicht angemeldet sind und Prüfung der Integrität Code aktiv ist, wie es normalerweise ist, erhalten Sie eine Fehlermeldung ähnlich der folgenden im Testfenster auszugeben.

``` syntax
* This is not a failure in CI, but a problem with the failing binary.
* Please contact the binary owner for getting the binary correctly signed.
```

 

 





