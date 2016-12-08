---
author: Justinha
Description: "Hinzufügen von Benutzeroberflächen-Sprachpaketen zu Windows"
ms.assetid: 6acfeb8f-ce94-46e0-b679-1f58958fdd3e
MSHAttr: PreferredLib:/library/windows/hardware
title: "Hinzufügen von Benutzeroberflächen-Sprachpaketen zu Windows"
ms.openlocfilehash: acdc3311f62d4cc2d6501e390da4a44b5de1b8bb
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-language-interface-packs-to-windows"></a>Hinzufügen von Benutzeroberflächen-Sprachpaketen zu Windows


Benutzeroberflächen-Sprachpakete (Benutzeroberflächen-Sprachpaketen) enthalten Windows Benutzeroberflächentext für einen Bereich. Benutzeroberflächen-Sprachpaketen müssen mit einer gültigen übergeordneten Sprache verwendet werden.

Beispielsweise das Katalanisch (ca-ES) LIP installiert werden kann nur, wenn eine der folgenden Sprachen bereits installiert ist: Englisch uns (En-US), Großbritannien (En-GB), Spanisch (es-ES) oder Französisch (fr-FR).

Um ein LIP Schwelle Windows offline hinzugefügt haben, müssen Sie sicherstellen, dass das unterstützte übergeordnete Language Pack zunächst an das Windows-Abbild installiert ist.

Eine Liste mit den Benutzeroberflächen-Sprachpaketen und deren übergeordnete Sprachen finden Sie unter [Verfügbaren Language Packs für Windows](available-language-packs-for-windows.md).

Die Version der LIP muss die Version von Windows übereinstimmen. Beispielsweise können nicht Sie ein Windows 10 LIP ein Bild Windows 8 oder Windows 8 LIP zu einem Windows-10-Abbild hinzufügen.

Für Windows 10 sind auch Language Packs und Benutzeroberflächen-Sprachpaketen zum Herunterladen von Windows Update verfügbar. Sie können zusätzliche Sprachen mithilfe **Der Systemsteuerung**hinzufügen. Für diesen Prozess muss Internet und Zugriff auf Windows Update. IT-Spezialisten und Endbenutzer können Windows Update zusätzliche Sprachen für ihre Windows-Installationen hinzufügen.

-   OEMs können anzeigen und Herunterladen von Benutzeroberflächen-Sprachpaketen von der [Microsoft OEM-Website](http://go.microsoft.com/fwlink/?LinkId=131359).
-   System-Builder können anzeigen und Herunterladen von Benutzeroberflächen-Sprachpaketen vom [OEM Partner Center](http://go.microsoft.com/fwlink/?LinkId=131358).
-   Benutzer können Sprachen oder Benutzeroberflächen-Sprachpaketen aus der Windows-Updates abrufen. Wechseln Sie zu **Einstellungen** &gt; **Uhrzeit- und Sprache** &gt; **Region & Sprache** &gt; **Hinzufügen einer Sprache**. Wählen Sie die Sprache aus, den, die Sie verwenden möchten, verwenden Sie aus der Liste und anschließend auf die Region-Version, die Sie verwenden möchten. Der Download wird sofort gestartet.

## <a name="span-idinstalllipsspanspan-idinstalllipsspanspan-idinstalllipsspaninstall-lips"></a><span id="Install_LIPs"></span><span id="install_lips"></span><span id="INSTALL_LIPS"></span>Installieren von Benutzeroberflächen-Sprachpaketen

**So installieren Sie ein LIP Verwendung des Überwachungsmodus (für manufacturing PCs verwendet)**

1.  Laden Sie das entsprechende LIP (und gegebenenfalls die Basissprache), und speichern Sie es auf das Wechselmedium.
2.  Starten Sie den Zielcomputer im Überwachungsmodus. Beispiel: auf dem Bildschirm OOBE drücken Sie STRG + UMSCHALT + F3 aus. Weitere Informationen finden Sie unter [Boot Windows im Überwachungsmodus oder OOBE](boot-windows-to-audit-mode-or-oobe.md).
3.  Das Wechselmedium, und Kopieren der LIP (und Ausgangssprache, falls erforderlich) auf den Zielcomputer.
4.  Wenn die Ausgangssprache nicht bereits installiert ist, installieren Sie es: Navigieren Sie zu der CAB-Datei, und doppelklicken Sie darauf. Führen Sie die Anweisungen, um die Installation abzuschließen.
5.  Installieren das LIP: Navigieren Sie zu der CAB-Datei, und doppelklicken Sie darauf. Führen Sie die Anweisungen, um die Installation abzuschließen.
6.  Beenden im Überwachungsmodus und Vorbereiten des PCs-Option für digitale Bilder oder die Bereitstellung, beispielsweise:

    Öffnen Sie ein Eingabeaufforderungsfenster und führen: 
    
    ``` syntax
    sysprep /oobe /generalize
    ``` 
    
    Weitere Informationen finden Sie unter [Sysprep (verallgemeinern) einer Windows-Installation](sysprep--generalize--a-windows-installation.md).

**So installieren Sie ein LIP zu einem offline Windows-Bild**

1.  Laden Sie das entsprechende LIP (und gegebenenfalls die Basissprache).
2.  Öffnen Sie eine Eingabeaufforderung mit erhöhten Berechtigungen.
3.  Stellen Sie das Windows-Abbild, dem Sie das LIP installieren möchten.

    ``` syntax
    md "C:\mount\windows"

    Dism /Mount-Image /ImageFile:C:\images\Win10\sources\install.wim /Index:1 /MountDir:"C:\mount\windows"
    ```

4.  Wenn die Basis LP, nicht bereits im Bild ist, fügen sie hinzu.

    ``` syntax
    Dism /Image:C:\mount\windows /Add-Package /PackagePath:C:\Languages\x64\langpacks\Microsoft-Windows-Client-Language-Pack_x64_es-es.cab
    ```

5.  Fügen Sie der LIP hinzu.

    ``` syntax
    Dism /Image:C:\mount\windows /Add-Package /PackagePath:C:\Languages\x64\langpacks\Microsoft-Windows-Client-Language-Interface-Pack_x64_ca-es.cab
    ```

6.  Wenn Sie Windows-setupmedien erstellen oder eine Freigabe Verteilung verwenden, erstellen Sie die lang.ini-Datei erneut.

    ``` syntax
    Dism /Image:C:\mount\windows /Gen-LangIni 
           /Distribution:C:\images\Win10\sources
    ```

    Die Datei "lang.ini" in C:\\Bilder\\Win10\\Quellen sollte etwa wie folgt aussehen:

    ``` syntax
    [Available UI Languages]
    ca-ES = 2
    es-ES = 3
     
    [Fallback Languages]
    es-ES = en-us
    ```

7.  Optional: Ändern Sie die Standardsprache, Gebietsschema und anderen internationalen Einstellungen in die lokale Sprache.

    ``` syntax
    Dism /image:C:\mount\windows /set-allIntl:ca-es
    ```

    Optional: Überprüfen Sie die Standardeinstellungen für internationale.

    ``` syntax
    Dism /image:C:\mount\windows /get-intl
    ```

    Beispielsweise sollte Ausgabe ähnlich der folgenden angezeigt:

    ``` syntax
    Reporting offline international settings.
     
    Default system UI language : es-ES
    System locale : ca-ES
    Default time zone : Romance Standard Time
    User locale for default user : ca-ES
    Location : Spain (GEOID = 217)
    Active keyboard(s) : 0403:0000040a
    Keyboard layered driver : PC/AT Enhanced Keyboard (101/102-Key)
     
    Installed language(s): ca-ES
      Type : Partially localized language, LIP type.
    Installed language(s): es-ES
      Type : Fully localized language.
     
    Reporting distribution languages.
     
    The default language in the distribution is:
    es-ES
    ```

8.  Hängen Sie das Bild, das geändert.

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\mount\windows /Commit
    ```

    Das Windows-Abbild kann jetzt bereitgestellt werden.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Hinzufügen von Language Packs zu Windows](add-language-packs-to-windows.md)

[Verfügbare Sprachpakete für Windows](available-language-packs-for-windows.md)

[Language Pack-Standardwerte](http://go.microsoft.com/fwlink/?LinkId=206622)

 

 






