---
author: Justinha
Description: "Hinzufügen von Support in mehreren Sprachen zu einer Windows-Verteilung"
ms.assetid: 2da53fc7-4c4d-4cea-9a98-0db4eacd33d2
MSHAttr: PreferredLib:/library/windows/hardware
title: "Hinzufügen von Support in mehreren Sprachen zu einer Windows-Verteilung"
ms.openlocfilehash: 891b373bfe0f974f7f751ff35a44725467befb94
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-multilingual-support-to-a-windows-distribution"></a>Hinzufügen von Unterstützung mehrerer Sprachen in eine Windows-Distribution


Windows® Setup können Sie eine mehrsprachige Edition von Windows bereitstellen. Hierbei handelt es sich um ein herkömmliches Szenario für Unternehmen, die Windows in einer mehrsprachigen Umgebung bereitstellen, in dem der Benutzer wechseln zwischen mehreren Sprachen auf einem einzelnen Computer die Anzeigesprache sein muss. Dieses Verfahren sind die folgenden Schritte erforderlich:

-   Kopieren Sie eine oder mehrere Sprachpakete in die ** \\Langpacks** Verzeichnis in der *Windows-Verteilung*. Die Windows-Verteilung wird der Inhalt des Windows Retail-DVD.

-   Aktualisieren Sie die Datei "lang.ini".

-   Verwenden Sie Setup die Language Packs zu installieren, die in der Freigabe der Verteilung sind.

**Wichtige**  
Hinzufügen von Language packs auf den ** \\Langpacks** Verzeichnis kann den Zeitpunkt der Windows-Setup-Installation zu erweitern. Pakete der ** \\Langpacks** Directory sind vor hinzugefügt, das Windows-Abbild während des Schritts **WindowsPE** Konfiguration Windows tatsächlich installiert ist. Wenn Windows Setup mehrere Sprachpakete installieren, müssen möglicherweise Installation verzögert.

 

**Zum Hinzufügen von Language Packs in einer Windows-Distribution**

1.  Kopieren der Windows-Verteilung in ein lokales Verzeichnis. Beispielsweise Kopieren Sie den Inhalt der Windows-Produkt-DVD in ein Verzeichnis mit dem Namen **C:\\meine\_Verteilung**.

2.  Suchen Sie die Language Pack CAB-Dateien für die Sprachen, die Sie für die Windows-Verteilung hinzufügen und in ein lokales Verzeichnis kopieren möchten. 

3.  Erstellen der ** \\Langpacks** Verzeichnis Verteilergruppe freigeben. Beispiel:

    ``` syntax
    mkdir C:\my_distribution\langpacks 
    ```

4.  Die Language packs Kopie der ** \\Langpacks** Verzeichnis der Verteilung Freigabe. Beispiel:

    ``` syntax
    mkdir C:\my_distribution\langpacks
    xcopy C:\LPs\Microsoft-Windows-Client-Language-Pack_x64_fr-fr.cab C:\my_distribution\langpacks\Microsoft-Windows-Client-Language-Pack_x64_fr-fr.cab
    ```

5.  (Optional) Kopieren Sie die lokalisierten Windows Setup Quellen auf die Verteilung Freigabe, um zusätzliche Sprachen im Windows-Setup verfügbar zu machen. Beispiel:

    ``` syntax
    xcopy E:\sources\fr-fr C:\my_distribution\sources\fr-fr /cherkyi 
    xcopy E:\sources\de-de C:\my_distribution\sources\de-de /cherkyi
    ```

    Dabei ist *E:* den Speicherort der Windows-Verteilung die lokalisierten Ressourcen für Windows Setup enthält.

    Die **/cherkyi** -Parameter für den Befehl **Xcopy** kopiert alle ausgeblendeten Dateien und Unterverzeichnisse und werden alle Dateien in das Zielverzeichnis überschrieben.

6.  Stellen Sie das Windows-Abbild, das in der Freigabe für die Verteilung ist. Dieser Schritt ist erforderlich für das Deployment Image Servicing and Management Tool (DISM.exe) zum Bericht der Liste der Sprachen, die in der WIM-Datei und die Datei "lang.ini" neu installiert werden. Verwenden Sie DISM, um das Windows-Abbild bereitzustellen. Beispiel:

    ``` syntax
    DISM.exe /Mount-Image /ImageFile:C:\my_distribution\sources\install.wim /index:1 /MountDir:C:\mount\windows
    ```

7.  Berichten der Sprachen, die in der Freigabe Verteilung verfügbar oder auf dem Windows-Abbild installiert sind, indem Sie mithilfe der **Option/Get-Intl** und zum Angeben der Freigabe Verteilung. Beispiel:

    ``` syntax
    DISM.exe /image:c:\mount\windows /distribution:c:\my_distribution /Get-Intl
    ```

    Stellen Sie sicher, dass die richtigen Sprachen als verfügbare Sprachen angezeigt werden und **die verfügbaren Sprachen in der Verteilung** die richtigen Sprachen anzuzeigen. Beispiel:

    ``` syntax
    Default system UI language : en-US
    System locale : en-US
    Default time zone : Pacific Standard Time
    User locale for default user : en-US
    Location : United States (GEOID = 244)
    Active keyboard(s) : 0409:00000409
    Keyboard layered driver : PC/AT Enhanced Keyboard (101/102-Key)

    Installed language(s): en-US
    Type : Fully localized language.

    Reporting distribution languages.

    The default language in the distribution is:
    en-US

    The other available languages in the distribution are:
    es-es, fr-fr
    ```

8.  Erstellen Sie die Datei "lang.ini" neu. Beispiel:

    ``` syntax
    DISM.exe /image:c:\mount\windows /Gen-LangINI /distribution:c:\my_distribution
    ```

    Wenn Sie hinzufügen oder von Sprachpaketen aus einer Windows-Verteilung entfernen, müssen Sie die Datei "lang.ini" neu erstellen. Die Lang.ini-Datei befindet sich im Quellenverzeichnis der Windows-Verteilung und während der Installation von Windows verwendet wird. Die lang.ini-Datei im Quellenverzeichnis sollte etwa wie folgt aussehen:

    ``` syntax
    [Available UI Languages]
    en-US = 3
    de-de = 0
    fr-fr = 0

    [Fallback Languages]
    en-US = en-us
    ```

    **Hinweis**  
    Sie können eine Sprache für die Windows-Installation von den auswählen, die in der Verteilung Freigabe verfügbar, beim Ausführen von Setup von einem vollständigen Betriebssystem nur sind. Wenn Sie Windows Setup für startbare Medien oder Windows PE ausführen, müssen Sie der Datei Boot.wim für mehrsprachige Unterstützung optionale Komponenten hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen von Unterstützung mehrerer Sprachen zu Windows Setup](add-multilingual-support-to-windows-setup.md).

     

9.  Heben Sie die Bereitstellung der WIM-Datei, und die Änderungen zu übernehmen. Beispiel:

    ``` syntax
    DISM.exe /Unmount-Image /MountDir:C:\mount\windows /commit 
    ```

    Sie können nun Windows Setup ausführen. Während der Installation werden Sie aufgefordert, eine der Sprachen auswählen, die Sie die Freigabe Verteilung hinzugefügt.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[DISM Sprachen und International Befehlszeilenoptionen zum Warten](dism-languages-and-international-servicing-command-line-options.md)

[Konfigurieren von internationalen Einstellungen in Windows](configure-international-settings-in-windows.md)

 

 






