---
author: kpacquer
Description: To get started, we'll create a basic Windows 10 IoT Core (IoT Core) image, flash it to a micro SD card, and put it into a device to make sure that everything's working properly.
ms.assetid: aeba79b8-d8dd-481a-a8bf-03ae28174632
MSHAttr: PreferredLib:/library
title: "Übung 1a: Erstellen eines grundlegenden Abbilds"
ms.openlocfilehash: f26acb8d359127a29b1499f4b1f772faa4d36400
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-1a-create-a-basic-image"></a>Übung 1a: Erstellen eines grundlegenden Abbilds

Zum Einstieg werde wir Erstellen eines einfaches Windows 10 IoT Core (IoT Core) Abbilds flash es zu einer micro SD-Karte und kopiert ihn in einem Gerät, um sicherzustellen, dass alles ordnungsgemäß funktioniert.

Wir werden einen Produktordner erstellen, der unsere ersten Entwurf darstellt. Für unsere erste Product entwerfen müssen wir nur genug für das IoT Core Gerät neu gestartet werden, und die integrierte OOBE app ausführen, das wir kann auf einem Monitor HDMI-kompatiblen sehen sein soll anpassen.

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>Erforderliche Komponenten

Finden Sie unter [Tools zum Anpassen von Windows IoT Core benötigt erhalten möchten](set-up-your-pc-to-customize-iot-core.md) , können Sie Ihre Techniker PC vorbereiten.

## <a name="span-idcreateabasicimagespanspan-idcreateabasicimagespanspan-idcreateabasicimagespancreate-a-basic-image"></a><span id="Create_a_basic_image"></span><span id="create_a_basic_image"></span><span id="CREATE_A_BASIC_IMAGE"></span>Erstellen eines grundlegenden Abbilds

**Legen Sie Ihren OEM-Namen (einmalige nur)**

-   Öffnen Sie die Datei **C:\\IoT-ADK-AddonKit\\Tools\\setOEM.cmd** in Notepad ein, und ändern Sie ihn mit den Namen Ihres Unternehmens. Wir haben diese Variable zur einfacheren Pakete mit Namen erstellen, leicht sind zu unterscheiden, aus denen von anderen Herstellern, mit dem Sie arbeiten, hinzugefügt.

    ``` syntax
    set OEM_NAME=Fabrikam
    ```

**Starten der IoT Core-Verwaltungsshell, wählen Sie Ihre Architektur und Installieren von Testzertifikaten**

1.  Wechseln Sie in Windows Explorer zu dem Ordner, in dem Sie die IoT Core ADK Add-Ons, beispielsweise installiert **C:\\IoT-ADK-AddonKit**, und öffnen Sie **IoTCoreShell.cmd**. Sie sollten Sie als Administrator ausführen aufgefordert.

    Der neue Wert für OEM\_NAME angezeigt werden soll, wenn Sie das Tool zu starten.
    
    Problembehandlung: Fehler: "das System nicht den angegebenen Pfad nicht gefunden". Wenn dies angezeigt wird, Maustaste auf das Symbol, und ändern im "Target" den Pfad zu dem Speicherort, den Sie ausgewählt haben, die Verwaltungstools installiert.

2.  **Umgebung für Architektur legen Sie** dazu aufgefordert werden wählen Sie 1 für ARM 2 für X86 oder 3 für X64, basierend auf der Architektur für die Übersichten, die Sie entwickeln werden. Angenommen, drücken Sie **1** zum Erstellen eines Bilds, das mit der Brombeere Pi 2 oder Brombeere Pi 3 kompatibel ist, oder **2** ein Image erstellt, das mit der Minnowboard Max kompatibel ist.

    Das Tool Einführung legt die Standard-Architektur und eine Versionsnummer für das Design, das Sie für zukünftige Updates verwenden können. Die Nummer der erste Version standardmäßig 10.0.0.0.

    (Warum eine vierteilige Versionsnummer? Informationen Sie zu Versioning Schemas in [Anforderungen zu aktualisieren](../../service/mobile/update-requirements.md).)

**Einmalige Aufgaben**

Diese Aufgaben müssen nur beim ersten Installieren von der IoT ADK AddonKit durchgeführt werden.

1.  Installieren von Zertifikaten für OEM-Test. Verwenden Sie diese zum Signieren der Testbinärdateien.

    ``` syntax
    InstallOEMCerts
    ```
    Die Zertifikate werden in den Stamm hinzugefügt. Finden Sie weitere Informationen finden Sie unter [Einrichten der signierenden-Umgebung](https://msdn.microsoft.com/library/windows/hardware/dn756804)
    
2.  Erstellen Sie alle in den Arbeitsordner Pakete.

    ``` syntax
    BuildPkg All
    ```
        
### <a name="span-idcreateatestprojectspancreate-a-test-project"></a><span id="Create_a_test_project"></span>Erstellen Sie ein Projekt

1.  Erstellen Sie einen neuen Produktordner. In diesem Ordner darstellt, ein neues Gerät wir erstellen möchten und Anpassung-Beispieldateien, mit denen wir unsere Projektanfang enthält.

    ``` syntax
    newproduct ProductA
    ```

    Dadurch wird den Ordner erstellt: C:\\IoT-ADK-AddonKit\\Quell -&lt;Bogen&gt;\\Produkte\\Produkt a angezeigt.

### <a name="span-idbuildanimagespanbuild-an-image"></a><span id="Build_an_image"></span>Erstellen eines Abbilds

1.  Ausschließen Sie Wechselspeicher Laufwerke, einschließlich der Micro SD-Karte und alle USB-Laufwerke.

2.  Ein Updatefunktion Testbild Verwendung von Standard-Dateien zu erstellen. Test-Bilder enthalten weitere Tools und Test Bilder mit entweder mit oder ohne Vorzeichen Test-Paketen erstellen.

    ``` syntax
    buildimage ProductA Test
    ```

    Dadurch wird eine FFU-Datei mit dem grundlegenden Abbild unter C: erstellt\\IoT-ADK-AddonKit\\erstellen\\&lt;Bogen&gt;\\Produkt a angezeigt\\Test.

    Problembehandlung:
    
    -  FEHLERCODES: 0 x 80070005 oder 0x800705b4: Öffnen Sie erneut die IoT Core-Verwaltungsshell als Administrator, trennen Sie alle externen Laufwerke (einschließlich micro SD-Karten und USB-Ziehpunkt Laufwerke), und versuchen Sie es erneut.  
    Wenn dies nicht funktioniert, gehen Sie zurück zum [festlegen einrichten den PC und Laden Sie die Beispiele](set-up-your-pc-to-customize-iot-core.md) , und stellen Sie sicher, dass alles installiert ist.

### <a name="span-idflashanimagespanflash-the-image-to-a-memory-card"></a><span id="Flash_an_image"></span>Das Bild auf einer Speicherkarte Flash

1.  Starten des **Windows IoT Core Dashboard**.

2.  Schließen Sie Ihre micro SD-Karte an Ihrem PC-Techniker, und wählen Sie ihn in das Tool.

3.  Wählen Sie **ein neues Gerät einrichten**, Gerätetyp: **benutzerdefinierte**.

4.  Aus, **die heruntergeladene Datei (Flash.ffu) an die SD-Karte Flash**, klicken Sie auf **Durchsuchen**, navigieren Sie zur Datei FFU (C:\\IoT-ADK-AddonKit\\erstellen\\&lt;Bogen&gt;\\Produkt a angezeigt\\Test\\ProductA.ffu), klicken Sie dann auf **Weiter**.

5.  Optional: Ändern der standardmäßigen Devicename (Standard ist Minwinpc.) 

6.  Geben Sie Ihr Gerät ein (der Standardwert lautet: p@ssw0rd).

7.  Akzeptieren der Lizenzbedingungen, und klicken Sie dann auf **Installieren**. Das Windows IoT Core Dashboard formatiert die micro SD-Karte und installiert das neue Bild.

### <a name="span-idtryitoutspantry-it-out"></a><span id="Try_it_out"></span>Probieren Sie es aus

1.  Verbinden Sie das Gerät IoT, wie etwa eine Brombeere Pi-2, in einen Monitor mit einem HDMI-Kabel.
    **Hinweis**  Verwenden Sie nach Möglichkeit eine direkte Verbindung mit einem HDMI Port. Die Anzeige möglicherweise nicht angezeigt, wenn DVI/VGA-Adapter oder Hubs verwenden.

2.  Tragen Sie die micro SD-Karte mit Ihrem Bild.

3.  Schalten Sie es.

    Nach kurzer während das Gerät automatisch gestartet werden sollte, und die [standardmäßige IoT Test-app](https://developer.microsoft.com/windows/iot/samples/iotdefaultapp) (mit dem Codenamen "Bertha"), die grundlegende Informationen über das Bild zeigt sollte angezeigt werden.

    **Hinweis**  Einige Geräte möglicherweise beim ersten Start starten können, wenn einige 8 GB Klasse 10 SD-Karten mit sehr langsam. Langsame Hochfahren möglicherweise als 15 Minuten dauern. Nachfolgenden Starts werden viel schneller auf den betroffenen Karten.

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>Nächste Schritte

Lassen Sie das Gerät auf jetzt, und fahren Sie mit [Übung 1 b: app hinzufügen, um das Bild](deploy-your-app-with-a-standard-board.md).