---
author: kpacquer
Description: Erstellen einer sicheren MMOS WIM-Bild
ms.assetid: c3ab9a94-a0a6-4831-9ac9-09c2972bb074
MSHAttr: PreferredLib:/library/windows/hardware
title: Erstellen einer sicheren MMOS WIM-Bild
ms.openlocfilehash: 3e1af1c21c4b8ea97fe3868483e03aabacff7f31
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="creating-a-secure-mmos-wim-image"></a>Erstellen einer sicheren MMOS WIM-Bild


Die SecWimTool können Sie eine sichere WIM-Abbild erstellen werden, die an Service Retail Geräte verwendet werden können.

Vor der Erstellung einer sicheren WIM müssen Sie zuerst das WIM-Abbild selbst erstellen. Informationen dazu, wie Sie ein WIM-Abbild erstellen finden Sie unter [Arbeiten mit WIM-MMOS Bilder](working-with-wim-mmos-images.md).

Um die MMOS WIM im Einzelhandel verwenden, muss er mit Retail Zertifikate signiert werden. Weitere Informationen erhalten in einer zukünftigen Version dieser Dokumentation über das Arbeiten mit den Bildern Retail.

Für die sichere WIM auf dem Gerät ausführen müssen die signierenden Zertifikate die Zertifikate in die Plattform Schlüssel (PK) übereinstimmen, die auf dem Gerät bereitgestellt wird.

## <a name="span-idinstallingtheneededcertificatesonthephonespanspan-idinstallingtheneededcertificatesonthephonespanspan-idinstallingtheneededcertificatesonthephonespaninstalling-the-needed-certificates-on-the-phone"></a><span id="Installing_the_needed_certificates_on_the_phone"></span><span id="installing_the_needed_certificates_on_the_phone"></span><span id="INSTALLING_THE_NEEDED_CERTIFICATES_ON_THE_PHONE"></span>Installieren die erforderlichen Zertifikate auf dem Telefon


Bevor Sie die Tools ausführen, müssen Sie zuerst die entsprechenden Zertifikate auf dem Gerät bereitstellen. Um mit SecWimTool vertraut sind, können Partner das sicheren Boot *Testen* Tool verwenden, Test (nicht Einzelhandel) Zertifikate auf dem Gerät bereit. Verwenden Sie das sichere Boot *Retail* -Tool für den Einzelhandel Gerät.

## <a name="span-idcreatingasecuremmoswimimagespanspan-idcreatingasecuremmoswimimagespanspan-idcreatingasecuremmoswimimagespancreating-a-secure-mmos-wim-image"></a><span id="Creating_a_secure_MMOS_WIM_image"></span><span id="creating_a_secure_mmos_wim_image"></span><span id="CREATING_A_SECURE_MMOS_WIM_IMAGE"></span>Erstellen einer sicheren MMOS WIM-Bild


Gehen Sie folgendermaßen vor, um einen sicheren WIM-Abbild zu erstellen.

1.  Öffnen einer Eingabeaufforderung mit erhöhten Rechten für Entwickler in das Verzeichnis, das die Ausgabe aus der ImgToWim Bild Generierungsprozess enthält. Informationen dazu, wie Sie ein WIM-Abbild erstellen finden Sie unter [Arbeiten mit Bildern WIM-MMOS](working-with-wim-mmos-images.md).

    **Hinweis**  
    Die Bild Generation ausführbare Dateien befinden sich im WPDKCONTENTROOT %\\Tools\\Bin\\i386. Sie können die `set` Befehl aus, um diesen Pfad zu Ihrer Umgebung hinzufügen.

     

2.  Die Plattform-ID muss verwendet werden, der für eine bestimmte Plattform WIM-DATEI zu erstellen. Die Plattform-ID wird festgelegt, sich mit einem Gerät Plattform XML-Datei.

    Sie können die Plattform-ID mit dem Befehl Ffutool und Anzeigen der **-Liste** Option.

    ``` syntax
    C:\> ffutool -list
    Name:   Contoso.DCD9X0X.BD301_ATT.3.2.1
    ID:     00000011-f151-a509-0000-FF0000000000
    ```

    Build der nicht signierte WIM Ziel Secure für eine bestimmte Plattform mit der *-Plattform* Befehlszeilenoption wie hier gezeigt. Keine Ausgabe wird zurückgegeben, wenn der Befehl erfolgreich ausgeführt wurde.

    ``` syntax
    C:\> SecWimTool -build MMOSwim.wim MMOS wim.secwim -platform Contoso.DCD9X0X.BD301_ATT.3.2.1
    ```

3.  Extrahieren Sie den Katalog aus dem sicheren WIM-Abbild. Keine Ausgabe wird zurückgegeben, wenn der Befehl erfolgreich ausgeführt wurde.

    ``` syntax
    C:\> SecWimTool -extractcat MMOSwim.secwim MMOSwim.cat
    ```

4.  Sie können das WIM mit Testzertifikate zum Testen des WIM-Prozess signieren. Für ein Retail müssen sichere WIM-DATEI, die FFU von Microsoft angemeldet sein.

    **Wichtige**  
    Informationen zum Anmelden mit den endgültigen Verkaufsversion Zertifikaten wird in einer zukünftigen Version der Dokumentation bereitgestellt.

    Verwenden Sie diesen Befehl, um den Katalog mit der Bild-Testzertifikat zu signieren.

    ``` syntax
    C:\> sign /pk MMOSwim.cat
    ```

    Mit diesem Befehl wird Ausgabe generiert, die die folgenden ähnelt.

    ``` syntax
    signtool.exe sign /v /a /u 1.3.6.1.4.1.311.76.5.10 /r "Microsoft Testing Root Certificate Authority 2010" /fd SHA256 /s my /c "1.3.6.1.4.1.311.21.8.7587021.7518
    74.11030412.6202749.3702260.207.4167089.4524209"    "MMOSwim.cat"
    The following certificate was selected:
        Issued to: User1
        Issued by: MSIT Test CodeSign CA 3
        Expires:   Sat Jun 21 15:05:01 2014
        SHA1 hash: F571C183F768638B424A59772A1AFB1168164AFC

    Done Adding Additional Store
    Successfully signed: MMOSwim.cat

    Number of files successfully Signed: 1
    Number of warnings: 0
    Number of errors: 0
    signed:  "MMOSwim.cat"
    Sign.Cmd RC=0
    ```

5.  Ersetzen Sie den vorhandenen Katalog mit einem Katalog mit Vorzeichen. Keine Ausgabe wird zurückgegeben, wenn der Befehl erfolgreich ausgeführt wurde.

    ``` syntax
    C:\> SecWimTool -replacecat flashwim.cat MMOSwim.secwim
    ```

6.  Platzieren Sie das Gerät im Modus blinken.

7.  Flash WIM auf das Gerät zum Testen der FFUTool verwenden.

    ``` syntax
    C:\> ffutool -wim MMOSwim.secwim
    ```

    Der Befehl generiert Ausgabe, ähnlich der folgenden ist.

    ``` syntax
    Found device:
    Name:   Contoso.MSM8X0X.BD301_ATT.3.2.1
    ID:     00000011-f151-a509-0000-FF0000000000
    Booting WIM: MMOSwim.secwim
    WIM transfer completed in 26.550073 seconds.
   
    ```

## <a name="span-idworkingwithserialnumbersspanspan-idworkingwithserialnumbersspanspan-idworkingwithserialnumbersspanworking-with-serial-numbers"></a><span id="Working_with_serial_numbers"></span><span id="working_with_serial_numbers"></span><span id="WORKING_WITH_SERIAL_NUMBERS"></span>Arbeiten mit der Seriennummer


Die Seriennummer Option kann verwendet werden, wenn einschließlich Tools, die nur für ein bestimmtes Gerät verwendet werden soll.

**Seriennummer**– die Seriennummer ist eine eindeutige ID für das Telefon, das automatisch generiert wird. Sie können die Seriennummer mit dem Befehl Ffutool und Anzeigen der *-serielle* Option.

``` syntax
C:\> ffutool -serial
Serial No. : 01000500000000000000000000001234
```

Verwenden Sie zum Erstellen einer sicheren WIM für ein bestimmtes Gerät vorgesehen sind die *– serial* Befehlszeilenoption, wie hier gezeigt.

``` syntax
C:\> SecWimTool -build MMOSwim.wim MMOS wim.secwim -serial 01000500000000000000000000001234
```

## <a name="span-idtroubleshootingspanspan-idtroubleshootingspanspan-idtroubleshootingspantroubleshooting"></a><span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Problembehandlung


Wenn Sie das Bild flash Wenn nicht der PK entspricht, wird diese Meldung.

``` syntax
An FFU error occurred: Device returned WIM boot failure status code 0x80000004.
```

## <a name="span-idsecwimtoolcommandlinereferencespanspan-idsecwimtoolcommandlinereferencespanspan-idsecwimtoolcommandlinereferencespansecwimtool-command-line-reference"></a><span id="SecWimTool_command_line_reference"></span><span id="secwimtool_command_line_reference"></span><span id="SECWIMTOOL_COMMAND_LINE_REFERENCE"></span>Befehlszeilenreferenz SecWimTool


Im folgenden werden die Befehlssyntax und die vier Befehlszeilenoptionen für SecWimTool zusammengefasst.

``` syntax
SecWimTool <command> <arguments>
```

**-build** -Packs der angegebenen WIM-DATEI in eine Secwim an, die für das Signieren und übertragen an einem Gerät Retail geeignet ist.

-   *Plattform* - umfasst adressieren Informationen für einen bestimmten Plattform, die für das WIM vorgesehen ist. Diese Option muss als Ziel der WIM-DATEI für eine bestimmte Plattform verwendet werden.

-   *Serial* - enthält die Seriennummer des ein bestimmtes Gerät, die in der WIM-DATEI verwendet werden soll. Diese Option kann verwendet werden, wenn Tools einschließen, die für ein bestimmtes Gerät nur verwendet werden soll.

``` syntax
SecWimTool -build <WIM> <output file> [-platform <ID>] [-serial <serial number>]
```

**-Extractcat** - Katalog aus der sicheren WIM-Datei abgerufen und schreibt sie in der Ausgabedatei (sofern angegeben) oder Stdout.

``` syntax
secwim -extractcat <path to .secwim> [<output file>]
```

**-Replacecat** - ersetzt Katalog in der angegebenen .secwim durch den Inhalt des neuen Katalogs.

``` syntax
secwim -replacecat <path to catalog> <path to .secwim>
```

**-?** -Zeigt Befehlszeilenhilfe. Verwenden Sie `secwimtool -<command> -?` Befehl Ebene Hilfe.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Arbeiten mit Bildern WIM MMOS](working-with-wim-mmos-images.md)

 

 






