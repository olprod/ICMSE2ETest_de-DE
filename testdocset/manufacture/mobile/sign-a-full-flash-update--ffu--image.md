---
title: "Melden Sie sich ein Bild vollständige flash-Update (FFU)"
description: "Sie müssen ein Bild FFU kryptografisch anmelden, bevor Sie es zu einem Gerät bereitstellen können. Dieser Schritt ist erforderlich, um Manipulation und bösartige Angriffe zu verhindern. Sie können nur Bilder auf einem Windows-10-Mobile-Gerät flash, nachdem sie ordnungsgemäß signiert werden."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 94761827-8c91-4477-9483-c61095151f90
ms.openlocfilehash: 0c5134f11b4af2859557d38bc92ca0f6a027f33c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sign-a-full-flash-update-ffu-image"></a>Melden Sie sich ein Bild vollständige flash-Update (FFU)


Sie müssen ein Bild FFU kryptografisch signieren, bevor Sie es zu einem Gerät bereitstellen können. Dieser Schritt ist erforderlich, um Manipulation und bösartige Angriffe zu verhindern. Sie können nur Bilder auf einem Windows-10-Mobile-Gerät flash, nachdem sie ordnungsgemäß signiert werden.

Der OEM muss das FFU Bild mit einem Zertifikat, dass mit den Startvorgang UEFI PK verkettet, die wichtige signiert ein OEM stellt diese bereit.

Der Entwicklungs-, Test-wird ein Testzertifikats das Bild FFU anstelle eines Zertifikats für den Einzelhandel signiert. Verwenden Sie das sichere Boot Test-Tool die entsprechenden Testzertifikate auf dem Gerät bereit

Retail Zertifikate werden für den Einzelhandel-Telefone auf dem Gerät mit Retail sicheren Boot Tools bereitgestellt.

## <a name="test-signing-images-using-windows-imaging-and-configuration-designer-icd"></a>Testen der signierenden Bildern mithilfe von Windows Imaging und Konfiguration Designer (ICD)


Nachdem Sie das sichere Boot Test-Tool verwenden, um die entsprechenden Testzertifikate bei einem Telefon bereitstellen, können Sie das Windows Imaging- und Konfiguration Designer (ICD) zum Generieren von Test signiert Bilder. Windows ICD wird automatisch Bilder, die mit dem richtigen Test Zertifikat signiert. Dies ist die empfohlene Vorgehensweise, die einfachste Methode, um ordnungsgemäß signierte Bilder vorbereiten unverändert. Weitere Informationen finden Sie unter [Windows ICD](https://msdn.microsoft.com/library/windows/hardware/dn916113).

## <a name="retail-signing-ffu-images"></a>Retail Signieren FFU Bilder


Bevor Bilder auf einem Gerät Retail geliefert werden können, müssen sie von Microsoft angemeldet sein. Verwenden der Schritte in diesem Abschnitt erstellen Sie eine Retail signierter FFU-Bilddatei, die für den Einzelhandel Geräte zugeordnet werden kann.

1.  Bevor Sie die Binärdateien anmelden können, müssen Sie zuerst die Test OEM-Zertifikate auf dem PC installieren, durch die Schritte in [der signierenden Umgebung eingerichtet](https://msdn.microsoft.com/library/windows/hardware/dn789236).

2.  Fügen Sie das Verzeichnis für das sign.cmd-Skript, die sich in WPDKCONTENTROOT % befindet\\Tools\\Bin\\i386 Ihrem Pfad mit dem Pfadbefehl.

    ``` syntax
    C:\> PATH = %PATH%;%WPDKCONTENTROOT%\Tools\bin\I386
    ```

3.  Öffnen Sie eine Aufforderung für Entwickler mit Administratorrechten in das Verzeichnis, das die Ausgabe aus der Generierungsprozess Bild enthält.

4.  Vergewissern Sie sich, dass Sie über die neueste Version des Kits, die aktualisierte Versionen von imagesigner.exe und imagecommon.dll umfasst haben, indem Sie den folgenden Befehl eingeben. Vergewissern Sie sich, dass die verkürzungsoption angezeigt wird.

    ``` syntax
    C:\> ImageSigner /?
    Usage:
            imagsigner sign <FFU> <catalog file>
            imagesigner getcatalog <FFU> <catalog file>
            imagesigner truncate <FFU> <truncated FFU>
    ```

    Wenn Sie keine aktuelle Version des Kit, die die aktualisierte ImageSigner enthält verfügen, herunterladen Sie und installieren Sie das neueste Kit.

5.  Extrahieren Sie die erste 1 MB des Bilds FFU enthält die FFU-Katalog und die zugehörigen Metadaten mithilfe der truncate Option.

    ``` syntax
    C:\> ImageSigner TRUNCATE OEM.ffu OEM.trunc
    ```

6.  Extrahieren Sie den Katalog aus dem abgeschnittene FFU Bild in Schritt 5 an.

    ``` syntax
    C:\> ImageSigner GETCATALOG OEM.trunc OEM.cat
    Platform ID: <OEMID>.QC8960.P728
    Successfully extracted catalog.
    C:\>
    ```

7.  Überprüfen, die &lt;OEMID&gt; zurückgegeben, in Schritt 6 ist identisch mit der OEMID zugewiesen, Sie von Microsoft. 

8.  Erstellen und ein TFS-Ticket der Microsoft-Kundendienst zum Signieren des Katalogs FFU übermitteln.  Stellen Sie sicher, dass Sie das abgeschnittene FFU Bild anfügen, das Sie in Schritt 4 erstellt haben.

    1.  Öffnen Sie ein *Update* Typ Ticket.

    2.  Geben Sie für den Titel Ticket *FFU Katalog Signierung anfordern von &lt;OEMID&gt;*. Geben Sie Ihre OEM-ID in die Kachel Ticket, in dem &lt;OEMID&gt; wird angezeigt.

    3.  Legen Sie die **Kategorie** auf *Aufnahme und Veröffentlichung*.

    4.  Legen Sie den **Problemtyp** auf *neu*.

9.  Microsoft wird die Anforderung verarbeiten und beheben das Ticket zurück an den OEM.  Innerhalb des Tickets aufgelöst wird Microsoft eine signierte Verkaufsversion des Katalogs FFU aus der ursprünglichen Ticket angefügte FFU abgeschnitten Bild extrahiert enthalten. In diesem Beispiel wird davon ausgegangen Sie, dass Microsoft signierten FFU Katalog mit dem Namen OEM.cat zurückgibt.

10. Signieren der FFU mit den Einzelhandel Microsoft signiert Katalogdatei mithilfe von ImageSigner an.

    ``` syntax
    C:\> ImageSigner SIGN OEM.ffu OEM.cat
    ```

11. Flash Retail signierten Retail Bilds auf einem Gerät, und stellen Sie sicher, dass es erwartungsgemäß verhält.

    ``` syntax
    C:\> FFUTool -flash OEM.ffu
    ```

12. Es kann nach Verkaufsversion signiertes Abbild getestet wurde für den Einzelhandel Geräte blinkt verwendet werden. Weitere Informationen finden Sie unter [Tools blinkt](flashing-tools.md) und [Verwendung der blinkende Tools von Microsoft bereitgestellt](use-the-flashing-tools-provided-by-microsoft.md).

**Wichtige**  
Sichere alle Verkaufsversion signiert Binärdateien bewährte branchenüblichen Methoden verwenden.

 

## <a name="test-signing-images-manually"></a>Test Bilder manuell zu signieren.


Wenn Ihre Entwicklungsumgebung Arbeit außerhalb Windows ICD umfasst, können Sie manuell Bildern mithilfe von sign.cmd signieren. Nachdem das Testzertifikat auf dem Gerät mit dem sicheren Boot Testtool bereitgestellt wurde, kann Sie können die Option /pk des Tools sign.cmd So melden Sie Bilder, die folgenden Schritte durchführen.

1.  Bevor Sie die Binärdateien anmelden können, müssen Sie durch die Schritte in [der signierenden Umgebung eingerichtet](https://msdn.microsoft.com/library/windows/hardware/dn789236)zuerst die Test OEM-Zertifikate auf dem Computer installieren.

2.  Fügen Sie das Verzeichnis für das sign.cmd-Skript, die sich in WPDKCONTENTROOT % befindet\\Tools\\Bin\\i386 Ihrem Pfad mit dem Pfadbefehl.

    ``` syntax
    C:\> PATH = %PATH%;%WPDKCONTENTROOT%\Tools\bin\I386
    ```

3.  Öffnen Sie eine Aufforderung für Entwickler mit Administratorrechten in das Verzeichnis, das die Ausgabe aus der Generierungsprozess Bild enthält.

4.  Extrahieren Sie den Katalog nicht signierte FFU-Datei.

    ``` syntax
    C:\> ImageSigner GETCATALOG TestSigned.FFU TestSigned.Cat
    ```

5.  Melden Sie sich mit der Option /pk Katalog.

    ``` syntax
    C:\> Set SIGN_OEM=1
    C:\> Sign.cmd /pk TestSigned.cat
    ```

6.  Signieren der FFU mit der signierte Katalogdatei ImageSigner verwenden.

    ``` syntax
    C:\> ImageSigner SIGN TestSigned.FFU TestSigned.Cat
    ```

## <a name="creating-custom-signed-images"></a>Erstellen benutzerdefinierte signierten Bilder


**Hinweis**  
Einige OEMs sollten benutzerdefinierte Tasten verwenden, um die Bilder zu verwalten. Diese Option ist komplexer und wird nicht empfohlen.

 

Wenn ein Bild erstellt wird, wird auch eine Datei zugeordneten Katalog erstellt. Diese Katalogdatei ist signiert und von dem Tool ImageSigner dann verwendet werden, um das Bild FFU signieren. Melden Sie sich die .cat-Datei mit einem Zertifikat, mit dem UEFI verkettet Schlüssel zu starten, die vom OEM bereitgestellt werden. Verschiedene Zertifikate werden für Test- und Einzelhandel Signieren verwendet.

Melden Sie sich die Katalogdatei mit einem entsprechenden Zertifikat durch die folgenden Schritte ausführen.

1.  Öffnen Sie eine Aufforderung für Entwickler mit Administratorrechten in das Verzeichnis, das die Ausgabe aus der Generierungsprozess Bild enthält. Weitere Informationen finden Sie unter [Erstellen eines Bildes mit ImgGen.cmd](building-a-phone-image-using-imggencmd.md).

2.  Test Signieren einer Katalogdatei mit dem Namen `TestRetailSigned.cat` mit einem Zertifikat mit dem Namen `TestCertName.pfx` durch den folgenden Befehl eingeben.

    ``` syntax
    C:\> SignTool sign /f TestCertName.pfx  TestRetailSigned.cat
    ```

    **Wichtige**  
    Sie sollten nur die signtool.exe mit der lokalen **Datei/f** -Option in einer Umgebung für Entwicklung intern verwenden. Wenn eine Hardware Security Module (HSM) verwendet wird, wird die **Option/CSP** verwendet, cryptographic Service Provider (CSP) an, den Container des privaten Schlüssels enthält. Befolgen Sie beim Signieren Updatepakete für das fertige Bild bewährte branchenüblichen Methoden.

     

3.  Erstellen Sie eine signierte .ffu-Datei aus der Datei nicht signierte .ffu und die passende signierte .cat-Datei mit dem Tool ImageSigner.exe.

    ``` syntax
    C:\> ImageSigner SIGN TestRetailSigned.FFU TestRetailSigned.Cat
    ```

## <a name="imagesigner-syntax-reference"></a>ImageSigner Syntax-Referenz


``` syntax
ImageSigner {SIGN|GETCATALOG|TRUNCATE} FFUFile CatalogFile|TruncatedFFU
```

-   **ANMELDUNG** – die **SIGN** -Aktion wird zum Signieren einer FFU-Datei verwendet.

-   **GETCATALOG** – die **GETCATALOG** -Aktion einen Katalog aus einer Datei FFU extrahiert und schreibt sie in einer Katalogdatei. Diese Option kann verwendet werden, um festzustellen, ob ein FFU ordnungsgemäß, vorbereitet wurde, indem Sie die extrahierten Katalogdatei mithilfe von Dateieigenschaften oder Tools wie SignTool untersuchen.

-   **ABSCHNEIDEN** – der truncate-Aktion wird verwendet, um eine abgeschnittene FFU erstellen.

-   *FFUFile* – den Pfad der Bilddatei FFU.

-   *CatalogFile* – der Pfad zu der Katalogdatei.

-   *TruncatedFFU* – der Pfad zu der abgeschnittene FFU-Datei.

## <a name="related-topics"></a>Verwandte Themen


[Erstellen von ein Telefon Bild mit ImgGen.cmd](building-a-phone-image-using-imggencmd.md)

 

 

[Senden Sie Kommentare zu diesem Thema an Microsoft] (mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Sign%20a%20full%20flash%20update%20%28FFU%29%20image%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Senden Sie Kommentare zu diesem Thema an Microsoft")





