---
author: Justinha
Description: "Hinzufügen und Entfernen von Sprachpaketen Offline mithilfe von DISM"
ms.assetid: 128cffa3-8c53-41c8-add2-fa10197f36a3
MSHAttr: PreferredLib:/library/windows/hardware
title: "Hinzufügen und Entfernen von Sprachpaketen Offline mithilfe von DISM"
ms.openlocfilehash: 984bfc6c78d7e5d887ff95b720124392ff628cf6
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-and-remove-language-packs-offline-using-dism"></a>Hinzufügen und Entfernen von Sprachpaketen Offline mithilfe von DISM


Alle Installationen von Windows® enthalten mindestens ein Language Pack und die sprachunabhängigen Binärdateien, die das Betriebssystem Core bilden. Dieses Thema enthält Informationen zur Verwendung von Abbildern Bereitstellung und Verwaltung (DISM.exe) zum Hinzufügen oder entfernen zusätzliche Language Packs und internationale Einstellungen konfigurieren. Sie können dasselbe Verfahren verwenden, zum Hinzufügen oder Entfernen von Benutzeroberflächen-Sprachpaketen (Benutzeroberflächen-Sprachpaketen). Weitere Informationen zum Unterschied zwischen ein Language Pack und der LIP finden Sie unter [Hinzufügen von Language Packs auf Windows](add-language-packs-to-windows.md).

Das Windows-Abbild muss ein kürzlich installiertes und Aktuelles Bild oder das Standardbild für den Einzelhandel. Dadurch wird sichergestellt, dass das Windows-Abbild ausstehenden Aktionen nicht vorhanden ist. Die Windows-Abbilder können in einer beliebigen Sprache sein. Beispielsweise können Sie mit einem Englisch (En-US) Abbild beginnen und Hinzufügen von Unterstützung für Japanisch (ja-JP) und Koreanisch (Ko-KR). Darüber hinaus können Sie Benutzeroberflächen-Sprachpaketen zu einem Windows-Abbild hinzufügen, die die unterstützte übergeordnete Sprache enthält. Weitere Informationen zu den unterstützten Language Packs und Benutzeroberflächen-Sprachpaketen finden Sie unter [Language Packs](language-packs-and-windows-deployment.md).

Dieses Thema enthält die folgenden Verfahren.

[Hinzufügen eines Sprachpakets zu einem Windows-Abbild](#addlangpacktoimage) wird beschrieben, wie ein neues Language Pack ein offline-Windows-Abbild hinzufügen.

[Entfernen eines Language Packs aus einem Windows-Abbild](#removelangpackfromwin) wird beschrieben, wie DISM verwenden, um ein Sprachpaket aus Schwelle Windows offline zu entfernen. Sie müssen alle Language Packs entfernen, die Sie nicht möchten, verwenden Sie vor dem Hinzufügen neuer Language Packs zu einem Windows-Abbild.

[Konfigurieren von internationalen Einstellungen](#configintlsettings) wird beschrieben, wie mithilfe von DISM ändern Sie die Standardsprache für die Anzeige und andere internationalen Einstellungen in einer Windows-Abbild konfigurieren.

Informationen zum Hinzufügen ein Sprachpakets zu einem Bild Windows Vorinstallation Environment (Windows PE) finden Sie unter Hinzufügen eines Sprachpakets zu einem Windows PE-Abbild.

## <a name="span-idaddlangpacktoimagespanspan-idaddlangpacktoimagespanspan-idaddlangpacktoimagespanadd-a-language-pack-to-a-windows-image"></a><span id="AddLangPacktoImage"></span><span id="addlangpacktoimage"></span><span id="ADDLANGPACKTOIMAGE"></span>Hinzufügen eines Sprachpakets zu einem Windows-Abbild


Language Packs stehen als CAB-Dateien und mit ihren Gebietsschema heißen; beispielsweise Microsoft-Windows-Client-Language-Pack_x64_es-es.cab. Als CAB-Dateien bereitgestellte Pakete können mithilfe des Befehlszeilentools DISM ein offline Windows-Abbild hinzugefügt werden. Dasselbe Verfahren können Sie ein Language Pack oder ein Language Interface Pack (LIP) hinzufügen.

**Wichtige**  
Benutzeroberflächen-Sprachpaketen sind als MLC-Dateien zur Verfügung. Wenn Sie ein LIP offline Windows Schwelle mithilfe des Befehlszeilentools DISM hinzufügen, müssen Sie die LIP-Datei von "LIP.mlc" zu "LIP.cab" umbenennen.

 

Benutzeroberflächen-Sprachpaketen können nur auf einem Windows-Abbild installiert werden, die der unterstützten übergeordneten Sprachen installiert hat. Beispielsweise kann der Baskisch (Baskisch) LIP nur auf einem Windows-Abbild installiert werden, die die Sprache Spanisch (Spanien) oder Französisch (Frankreich) übergeordnete Language Pack installiert wurde. Vor der Installation der LIP zu einem offline Windows Bild stellen Sie sicher, dass die unterstützten übergeordneten Sprachen installiert sind. Weitere Informationen zu den unterstützten Language Packs und Benutzeroberflächen-Sprachpaketen finden Sie unter [Language Packs](language-packs-and-windows-deployment.md).

Sie können auch eine Antwortdatei Language Packs und Benutzeroberflächen-Sprachpaketen hinzufügen und dann die Antwortdatei zu einem offline Windows Bild anwenden. Wenn Sie dies tun, können Sie in den gleichen Vorgang der LIP und übergeordnete Sprache installieren.

**Wichtige**  
Installieren Sie ein Language Pack nicht nach einer Aktualisierung. Wenn Sie ein Update installieren (Hotfix, allgemein verfügbare Version \[GDR\], oder Servicepack \[SP\]), die Language-abhängigen Ressourcen enthalten soll, bevor Sie ein Sprachpaket installieren, die sprachspezifische Änderungen, die in dem Update enthalten sind, nicht übernommen werden und Sie das Update zu installieren müssen. Installieren Sie Sprachpakete immer vor der Installation von Updates.

 

**So fügen Sie ein Language Pack mithilfe von DISM hinzu**

1.  Vor dem Hinzufügen neuer Language Packs zu einem Windows-Abbild, müssen Sie alle Language Packs vom Windows-Abbild entfernen, die Sie nicht verwenden möchten. Weitere Informationen finden Sie unter [Entfernen eines Language Packs aus einem Windows-Abbild](#removelangpackfromwin).

2.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

3.  Wenn Ihr Bild aus dem letzten Verfahren bereits bereitgestellt ist, können Sie eingeben, den folgenden Befehl aus, um die Bilder aufzulisten, die derzeit bereitgestellten und Informationen zu den bereitgestellten Abbild wie Bereitstellungsort und Index des bereitgestellten Abbilds.

    ``` syntax
    Dism /Get-MountedImageInfo
    ```

    Wenn das Abbild nicht bereitgestellt wird, geben Sie den folgenden Befehl zum Abrufen der Name oder die Indexnummer für das Bild, das Sie ändern möchten.

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images\install.wim
    ```

    Ein Index oder Name-Wert ist erforderlich für die meisten Vorgänge, die Bilddatei festlegen. Geben Sie den folgenden Befehl zum Bereitstellen des Abbilds.

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Name:"Windows 7 HomeBasic" /MountDir:C:\test\offline
    ```

4.  Geben Sie den folgenden Befehl zum Hinzufügen eines Language Packs auf das bereitgestellte Abbild offline. Sie können mehrere Pakete über eine Befehlszeile hinzufügen.

    ``` syntax
    Dism /Image:C:\test\offline /ScratchDir:C:\Scratch /Add-Package /PackagePath:C:\packages\package1.cab /PackagePath:C:\packages\package2.cab ...
    ```

    **Hinweis**  
    Das temporäre Verzeichnis muss mindestens 1 GB für das Hinzufügen von Language Packs.

5.  Geben Sie den folgenden Befehl aus, um die Änderungen zu übernehmen. Das Bild bleibt eingebundene erst die Option **/ heben Sie die Bereitstellung** verwendet wird.

    ``` syntax
    Dism /Commit-Image /MountDir:C:\test\offline
    ```

6.  Die Sprachpakete werden die Windows-Abbild hinzugefügt. Im nächste Schritt werden [Internationalen Einstellungen konfigurieren](#configintlsettings).

**So fügen Sie ein Language Pack mithilfe einer Antwortdatei und DISM hinzu**

1.  Notieren Sie den Speicherort der Sprachpakete Sie das Windows-Abbild hinzufügen möchten. Language Packs werden in CAB-Dateien gespeichert.

2.  Verwenden Sie Windows SIM eine Antwortdatei erstellen, die nur die Language Packs enthält, die Sie hinzufügen möchten. Weitere Informationen zur Erstellung eine Antwortdatei finden Sie unter [Erstellen oder eine Antwortdatei öffnen](https://msdn.microsoft.com/library/windows/hardware/dn915085).

3.  Im Knoten **Paket** unter **Language Packs**mit der rechten Maustaste in des Sprachpakets, das Sie hinzufügen möchten, und wählen Sie dann **zur Antwortdatei hinzufügen**aus.

4.  Wählen Sie im Bereich **Eigenschaften** unter **Einstellungen** **Installieren** Wert für die Einstellung der **Aktion** ein.

5.  Sie können auch in die Antwortdatei internationale Einstellungen konfigurieren. Weitere Informationen finden Sie unter [Configure International Settings in Windows](configure-international-settings-in-windows.md).

6.  Überprüfen Sie, und speichern Sie die Antwortdatei.

7.  Schließen Sie Windows System Image Manager.

    **Wichtige**  
    Stellen Sie sicher, dass das Language Pack auf den in die Antwortdatei angegebenen Speicherort kopiert werden.

     

8.  Wenn das Abbild nicht bereits bereitgestellt ist, verwenden Sie DISM, um das Windows-Abbild bereitzustellen. Beispielsweise

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Index:1 /MountDir:C:\test\offline
    ```

9.  Verwenden Sie DISM, um die Antwortdatei für die unbeaufsichtigte Installation auf das bereitgestellte Windows-Abbild anzuwenden. Beispielsweise

    ``` syntax
    DISM /Image:C:\test\offline /Apply-Unattend:C:\test\answerfiles\myunattend.xml
    ```

    Weitere Informationen zum Anwenden eine Antwortdatei mithilfe von DISM, finden Sie unter [DISM Befehlszeilenoptionen zum Warten](dism-unattended-servicing-command-line-options.md).

10. Die Sprachpakete werden hinzugefügt, auf dem Windows-Abbild, und internationale Einstellungen konfiguriert werden.

## <a name="span-idremovelangpackfromwinspanspan-idremovelangpackfromwinspanspan-idremovelangpackfromwinspanremove-a-language-pack-from-a-windows-image"></a><span id="RemoveLangPackfromWin"></span><span id="removelangpackfromwin"></span><span id="REMOVELANGPACKFROMWIN"></span>Entfernen eines Language Packs aus einem Windows-Abbild


Vor dem Hinzufügen neuer Language Packs zu einem Windows-Abbild, müssen Sie alle Language Packs entfernen, die Sie nicht verwenden möchten. Es gibt zwei Methoden, um Language Packs im Offlinemodus mit DISM entfernen. Sie können entweder eine Antwortdatei auf offline-Abbild anwenden, oder Sie können das Sprachpaket direkt entfernen, aus dem Bild offline, mithilfe der Befehlszeile.

**Wichtige**  
Sie können nicht aus einer Windows-Abbild offline online Aktionen ausstehen ein Language Pack entfernen. Das Windows-Abbild muss ein kürzlich installiertes und aktuelles Abbild handeln. Dadurch wird sichergestellt, dass das Windows-Abbild keine ausstehenden online Aktionen, die ein Neustart erforderlich.

 

**So entfernen ein Language Pack mithilfe von DISM**

1.  Suchen Sie den Windows WIM-Datei oder eine virtuelle Festplatte (VHD- oder .vhdx), die das Windows-Abbild enthält, dem Sie Sprachen entfernen möchten.

2.  Klicken Sie auf **Start**, und geben Sie die **Bereitstellung**. Mit der rechten Maustaste **Bereitstellung und Imaging Tools Umgebung** , und wählen Sie dann auf **als Administrator ausführen**.

3.  Geben Sie in der Befehlszeile den folgenden Befehl zum Abrufen der Name oder die Indexnummer für das Bild, das Sie ändern möchten.

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images\install.wim 
    ```

    Ein Index oder Name-Wert ist erforderlich für die meisten Vorgänge, die Bilddatei festlegen.

4.  Geben Sie den folgenden Befehl zum Bereitstellen von offline-Windows-Abbild.

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Name:"Windows 7 HomeBasic" /MountDir:C:\test\offline
    ```

5.  Optional: Geben Sie den folgenden Befehl aus, um die Sprachen in der offline-Abbild aufzulisten.

    ``` syntax
    Dism /Image:C:\test\offline /Get-Intl
    ```

6.  Geben Sie den folgenden Befehl zum Entfernen eines Language Packs aus dem Bild. Sie können mehrere CAB-Dateien mit einem Command-Line-Anweisung entfernen.

    ``` syntax
    Dism /Image:C:\test\offline /Remove-Package /PackagePath:C:\packages\package1.cab /PackagePath:C:\packages\package2.cab ...
    ```

7.  Geben Sie den folgenden Befehl aus, um die Änderungen zu übernehmen. Das Bild bleibt eingebundene, bis die Option **/ heben Sie die Bereitstellung** verwendet wird.

    ``` syntax
    Dism /Commit-Image /MountDir:C:\test\offline
    ```

8.  Die Sprachpakete werden aus dem Abbild entfernt. Im nächste Schritt wird das bereitgestellte offline-Abbild ein Language Pack hinzugefügt. Finden Sie unter [Hinzufügen eines Sprachpakets zu einem Windows-Abbild](#addlangpacktoimage), um den Vorgang fortzusetzen.

**So entfernen ein Language Pack mithilfe von DISM und einer Antwortdatei**

1.  Mithilfe von Windows® System Image Manager (Windows SIM) zum Erstellen einer Antwortdatei, die nur die Language Packs enthält, die Sie entfernen möchten. Öffnen Sie das Windows-Abbild mithilfe von Windows SIM, und erstellen Sie eine neue Antwortdatei. Weitere Informationen dazu, wie Sie mithilfe von Windows SIM finden Sie unter [Erstellen oder eine Antwortdatei öffnen](https://msdn.microsoft.com/library/windows/hardware/dn915085).

2.  Die **Package** -Knoten, klicken Sie unter **Language Packs**mit der Maustaste des Sprachpakets, das Sie entfernen, und wählen Sie **zur Antwortdatei hinzufügen**möchten.

3.  Wählen Sie im Bereich **Eigenschaften** unter **Einstellungen für**den Wert **Entfernen** , für die Einstellung der **Aktion** ein.

4.  Speichern Sie die Antwortdatei, und schließen Sie Windows SIM. Die Antwortdatei muss dem folgenden Beispiel ähneln.

    ``` syntax
    <package action="remove">
       <assemblyIdentity name="Microsoft-Windows-LanguagePack-Package" version="6.0.5714.0" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="en-US" />
    </package>
    ```

5.  Binden Sie das Windows-Abbild mithilfe von DISM. Beispielsweise

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Index:1 /MountDir:C:\test\offline
    ```

6.  Verwenden Sie DISM, um die Antwortdatei für die unbeaufsichtigte Installation auf das bereitgestellte Windows-Abbild anzuwenden. Beispielsweise

    ``` syntax
    Dism /Image:C:\test\offline /Apply-Unattend:C:\test\answerfiles\myunattend.xml
    ```

    Weitere Informationen zur Verwendung von DISM anwenden eine Antwortdatei finden Sie unter [DISM Befehlszeilenoptionen zum Warten](dism-unattended-servicing-command-line-options.md).

7.  Geben Sie den folgenden Befehl aus, um die Änderungen zu übernehmen. Das Bild bleibt eingebundene erst die Option **/ heben Sie die Bereitstellung** verwendet wird.

    ``` syntax
    Dism /Commit-Image /MountDir:C:\test\offline
    ```

8.  Die Sprachpakete werden aus dem Abbild entfernt. Im nächste Schritt wird das bereitgestellte offline-Abbild ein Language Pack hinzugefügt. Finden Sie unter [Hinzufügen eines Sprachpakets zu einem Windows-Abbild](#addlangpacktoimage), um den Vorgang fortzusetzen.

## <a name="span-idconfigintlsettingsspanspan-idconfigintlsettingsspanspan-idconfigintlsettingsspanconfigure-international-settings"></a><span id="ConfigIntlSettings"></span><span id="configintlsettings"></span><span id="CONFIGINTLSETTINGS"></span>Konfigurieren von internationalen Einstellungen


Nach dem Hinzufügen oder eines Language Packs in einer Windows-Abbild entfernen, können Sie die Standardsprache der Benutzeroberfläche (UI), festlegen, die auch bekannt als der Anzeigesprache ist. Zur selben Zeit können Sie die internationalen Einstellungen im Windows-Abbild mithilfe von DISM konfigurieren.

Sie können auch in einer Antwortdatei internationale Einstellungen konfigurieren. Weitere Informationen hierzu finden Sie unter [Configure International Settings in Windows](configure-international-settings-in-windows.md).

**Hinweis**  
Wenn Sie eine standardmäßige Benutzeroberflächensprache und Gebietsschema, indem Sie das Tool DISM angeben, und Sie dann in einer Antwortdatei andere Sprache und Gebietsschema geben, überschreiben die Einstellungen in die Antwortdatei die durch das Tool DISM angegebenen Standardwerte festgelegt.

 

**So konfigurieren Sie mithilfe von DISM internationale Einstellungen**

1.  Wenn es nicht bereits bereitgestellt ist, müssen Sie zunächst das Bild bereitstellen. Beispielsweise

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Index:1 /MountDir:C:\test\offline
    ```

2.  Geben Sie den folgenden Befehl, um alle internationale spracheinstellungen im bereitgestellten offline-Abbild die Standardwerte von Microsoft für eine bestimmte Sprache, an der Befehlszeile DISM festgelegt entsprechend zu ändern,

    ``` syntax
    Dism /Image:C:\test\offline /Set-SKUIntlDefaults:en-us
    ```

    **Hinweis**  
    Die **Option/Set-SKUIntlDefaults** den Tastaturtreiber für japanische und koreanische Tastaturen nicht geändert. Sie müssen die **Option/Set-layereddriver** verwenden, um dies zu ändern. Weitere Informationen finden Sie unter [DISM Sprachen und International Befehlszeilenoptionen zum Warten](dism-languages-and-international-servicing-command-line-options.md).

     

    Weitere Informationen zu Standardwerten finden Sie unter [Windows Language Pack-Standardwerte](windows-language-pack-default-values.md).

    Optional können Sie unterschiedliche Werte für verschiedene Einstellungen, einschließlich Benutzeroberfläche Sprache, Systemgebietsschema, Benutzergebietsschema, das Gebietsschema und andere Benutzer konfigurieren. Weitere Informationen zum Angeben von einzelnen Werte für jede dieser Einstellungen finden Sie unter [DISM Sprachen und internationalen Befehlszeilenoptionen zum Warten](dism-languages-and-international-servicing-command-line-options.md).

3.  Geben Sie an einer Eingabeaufforderung den folgenden Befehl ein, und heben Sie die Bereitstellung des Abbilds commit der Änderungen.

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

Das Windows-Abbild kann jetzt bereitgestellt werden.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Hinzufügen von Language Packs zu Windows](add-language-packs-to-windows.md)

[Ein Windows-Abbild mithilfe von DISM-Service](service-a-windows-image-using-dism.md)

[DISM - Bereitstellung Bild Wartung und Verwaltung technische Referenz für Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

[DISM Sprachen und International Befehlszeilenoptionen zum Warten](dism-languages-and-international-servicing-command-line-options.md)

[DISM unbeaufsichtigtes Befehlszeilenoptionen zum Warten](dism-unattended-servicing-command-line-options.md)

[Technische Referenz zu Windows System Image Manager](https://msdn.microsoft.com/library/windows/hardware/dn922445)

 

 






