---
author: Justinha
Description: "Abrufen von Tools zum Anpassen von Windows benötigt"
ms.assetid: a52b4efe-ead0-4319-ae19-799d4e9d9e7b
MSHAttr: PreferredLib:/library/windows/hardware
title: "Abrufen der erforderlichen Tools für die Windows anpassen"
ms.openlocfilehash: fe6e727e80712af4385014dfeb61f8ba1384a8d5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-the-tools-needed-to-customize-windows"></a>Abrufen von Tools zum Anpassen von Windows benötigt


Nachfolgend finden Sie die erforderlichen zum Testen und Bereitstellen von Geräten zu starten:

## <a name="span-idpcspanspan-idpcspanpcs"></a><span id="pc"></span><span id="PC"></span>PCs


Sieht aus wie wir auf diese verwiesen wird:

-   **Techniker PC**: Ihre Arbeit PC. Diesem PC sollte mindestens 15 GB freiem Speicherplatz für die Installation von [Windows Assessment and Deployment Kit (Windows ADK)](http://go.microsoft.com/fwlink/?LinkId=526803) und zum Ändern von Windows-Abbildern verfügen. Es wird empfohlen, mithilfe von Windows 10 oder Windows 8.1 mit den neuesten Updates. Die Mindestanforderung ist Windows 7 Service Pack 1, obwohl das für Aufgaben wie das Bereitstellen zusätzlicher Tools oder problemumgehungen erfordert. ISO-Bilder.

    Für die meisten Aufgaben können entweder eine X86 oder X64 PC. Bei Erstellung X86 Bilder, benötigen Sie ein X86-PCs für eine bestimmte einmalige Aufgabe, [generieren eine Katalogdatei für X86-basierte PCs](update-windows-settings-and-scripts-create-your-own-answer-file-sxs.md).

-   **Referenz-Gerät**: A test PC oder Tablet, die alle Geräte in ein einziges Modell Linie darstellt Angenommen, die *Fabrikam Notizbuch PC Datenreihe 1*. Dieses Gerät muss die Windows-10-Mindestanforderungen erfüllen.

    Sie können dieses Gerät als Teil der exemplarischen Vorgehensweise neu formatieren.

## <a name="span-idhwspanspan-idhwspanstorage"></a><span id="hw"></span><span id="HW"></span>Speicher


-   **Windows PE USB-Schlüssel**: muss mindestens 512 MB und höchstens 32 GB. Dieses Laufwerk formatiert, Ihre Daten Abmelden zunächst speichern. Es sollte keinen Schlüssel Windows für unterwegs oder einen Schlüssel, der als nicht Wechseldatenträger gekennzeichnet sein.

-   **Speicher USB-Schlüssel** (USB-B): eine zweite Taste USB oder eine externe USB-Festplatte zum Speichern von Dateien. Minimaler freier Speicherplatz: 8GB, bei Verwendung von NTFS, ExFAT oder ein anderes Dateisystem, die mehr als 4 GB Dateien ermöglicht.  Wenn Ihre Hardware zulässig ist, verwenden Sie 3.0 USB-Schlüssel/Laufwerke und USB-3.0 Ports, um die Datei Kopierverfahren zu beschleunigen. Beachten Sie, dass einige 3.0 USB-Schlüssel nicht mit einigen USB 2.0-Anschlüsse funktionieren. Es wird nicht formatieren dieses Laufwerk, sodass solange Sie genügend Speicherplatz verfügen, können Sie eine vorhandene Speicherlaufwerk wiederverwenden. 

## <a name="span-idswspanspan-idswspansoftware"></a><span id="sw"></span><span id="SW"></span>Software

Kopieren Sie die folgenden Quelldateien auf dem PC-Techniker, anstatt externe Quellen wie Netzwerkfreigaben oder Wechseldatenträgern. Dies verringert das Risiko unterbrechen Buildvorgang aus ein Problem mit der temporären oder das USB-Gerät zu trennen.

Rufen Sie zum Ausführen dieses Handbuchs die empfohlene Downloads in diesem Abschnitt aus <https://www.microsoftoem.com>. 

Die Versionsnummern des Windows ADK, das Windows-Abbild sind Sie bereitstellen, und der Sprachen und Features, die Sie hinzufügen möchten, müssen übereinstimmen.

Diese Übungseinheit geht davon aus, die 64-Bit-Architektur, wenn Sie die 32-Bit-Version verwenden, ändern Sie alle Vorkommnisse des X64 zu X86.

### <a name="windows-10-version-1607-image-installwim"></a>Windows 10, Version 1607 Bild (install.wim)

|  |  |
|-----------|----------------------------------------------------|
| X21 08790 | Windows Home 10, Version 1607 32/64 English OPK    |
| X21 08794 | Windows Home SL 10, Version 1607 32/64 English OPK |
| X21 08798 | Windows Pro 10, Version 1607 32/64 English OPK     |

-   Binden Sie die ISO-Datei auf einem Laufwerk, und notieren Sie der Buchstabe des Laufwerks, z. B. D.

-   Kopieren Sie die D:\\Quellen\\install.wim Datei, und speichern Sie es auf dem lokalen Laufwerk, in den Ordner: **C:\\Bilder\\Win10\_X64\\**.

### <a name="windows-assessment-and-deployment-kit-adk-for-windows-10-version-1607"></a>Windows Assessment and Deployment Kit (ADK) für Windows 10, Version 1607

[Windows ADK für Windows 10, Version 1607](http://go.microsoft.com/fwlink/?LinkId=526803) oder X21 05999: 10 ADK gewinnen

### <a name="customizations-windows-updates-languages-features-apps-and-microsoft-office"></a>Anpassungen: Windows-Updates, Sprachen, Funktionen, apps und Microsoft Office

|  |  |
|-----------|---------------------------------------------------|
| X21 08801 | Win 10 1607 32/64 mehrsprachige OPK LangPackAll/LIP   |
| X21 08802 | Win 10 1607 32/64 mehrsprachige OPK Feat bei Bedarf    |
| X21 08808 | Win 10 1607 32/64 mehrsprachige OPK App-Update        |
| X21 19559 | 10 1607 OPK ZDP gewinnen                               |
| X20 98485 | Office Mobile mehrsprachige v1. 3 OPK                  |
| X21 05453 | Office 2016 v16.2-Bereitstellungstool für OEM OPK     |
| X21 05414 | Office 2016 v16.2 englische OPK                     |
| X21 05508 | Office v16.2 Deutsch OPK                           |

Außerdem besprochen, wie Sie Hardware-Treiber und andere Windows-apps in diesem Handbuch hinzufügen, abrufen, die von den Herstellern Hardware und Software.

### <a name="product-keys"></a>Die Product keys

Rufen Sie die Standard-Product Keys für die einzelnen Windows-Versionen der Kit Handbuch Windows 10 Standard Manufacturing Schlüssel OEM PDF-Datei, auf die ISO mit dem Windows-Abbild.

Rufen Sie die Verteilung die Product Keys, die mit dem Windows 10 Bild übereinstimmen.

### <a name="sample-files-create-a-deployment-usb-drive"></a>Beispieldateien: Erstellen einer Bereitstellung USB-Laufwerk

1.  Formatieren Sie ein USB-Laufwerk mit dem NTFS-Dateiformat, nennen Sie sie USB-B.

    ![Extrahieren von USB](images/extract-usb.png) 

2.  Laden Sie die meisten Lab Beispiele von [USB-B.zip](http://download.microsoft.com/download/5/8/4/5844EE21-4EF5-45B7-8D36-31619017B76A/USB-B.zip), und extrahieren Sie die Dateien auf dem Laufwerk.

    Fügen Sie dies die [neuere Version der Bereitstellung Beispielskripts](http://go.microsoft.com/fwlink/p/?LinkId=800657)hinzu. 

## <a name="span-idpreparespanspan-idpreparespanprepare-your-technician-pc"></a><span id="prepare"></span><span id="PREPARE"></span>Vorbereiten Sie Ihrer PC-Techniker

Hier wird zum Einrichten von Ihrem PCs.

**Kopieren Sie das Windows-Abbild auf dem lokalen Laufwerk**

1.  Bereitstellen die Windows-ISO-Datei, die Sie heruntergeladen haben (mit der rechten Maustaste in der Datei &gt; **Bereitstellen**), und notieren Sie den Laufwerkbuchstaben, beispielsweise D.

2.  Erstellen Sie einen neuen Ordner im Datei-Explorer (Beispiel: **C:\\Bilder\\Win10\_X64**), und kopieren Sie das Windows-Abbild (D:\\Quellen\\install.wim) Datei in den Ordner. Dies hilft höher auf Geschwindigkeit Verfahren zum Erstellen von Datei.

**Installieren Sie das Windows ADK für Windows 10**

1.  Wenn Sie eine frühere Version von Windows Assessment and Deployment Kit (ADK) verfügen, deinstallieren Sie es.

2.  Laden Sie die Version von [Windows ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit#winADK) , die mit der Windows-Version übereinstimmt, die Sie installieren möchten. **Führen** Sie das Installationsprogramm.

3.  Klicken Sie auf **Weiter** &gt; **nächsten** &gt; **annehmen** , die Standardeinstellungen zu übernehmen und an das Programm zur Verbesserung der Benutzerfreundlichkeit teilnehmen.

4.  Wählen Sie die folgenden Tools:

    -   **Bereitstellungstools**

    -   **Vorinstallation Windows-Umgebung (Windows PE)**

    -   **User State Migrationstool (USMT)**

    Für diesen Übungseinheiten brauchen Sie keine das **Windows Performance Toolkit** oder das **Windows Assessment Toolkit**. Sie können diese Kontrollkästchen deaktivieren.

5.  Klicken Sie auf **Installieren**, und klicken Sie dann auf **Ja** , zu bestätigen. Dies kann einige Minuten dauern.

6.  Wenn die Installation abgeschlossen ist, klicken Sie auf **Schließen**.

Nächster Schritt: [Übung 1: Installieren von Windows PE](install-windows-pe-sxs.md)
