---
Description: You can now easily configure the default Start layout to include Web links, secondary tiles, folders, and apps. The converged Windows 10 Start layout requires that you create a LayoutModification.xml file, which we'll create in this walkthrough.
ms.assetid: 99238b56-5c9c-4b5e-a750-e64a10e417af
MSHAttr: PreferredLib:/library
title: Konfigurieren des Start-Layouts
author: CelesteDG
ms.openlocfilehash: 82d6babe0297b290a3da03f37a5ab34afc390446
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-the-start-layout"></a>Konfigurieren des Start-Layouts


Sie können jetzt das Standardlayout Start zum Einschließen von Weblinks, sekundäre Kacheln, Ordner und apps auf einfache Weise konfigurieren. Das zusammengeführt Windows 10 starten Layout erfordert, dass Sie eine Datei LayoutModification.xml erstellen, die erstellen wir in dieser exemplarischen Vorgehensweise.

**Hinweis**  Das Schema für die Datei LayoutModification.xml unterscheidet sich von der MCSF Anpassung Antwort Dateischema oder Windows provisioning Antwort Dateischema. Sie müssen die LayoutModification.xml verwenden, um vollständig die Start-Anpassung Windows 10 nutzen und können die Start-Einstellungen in MCSF oder Windows-Bereitstellung so verweisen Sie auf LayoutModification.xml.

 

Wenn Sie nicht neu in Windows mobile Entwicklung sind und wurden bereits vorhandene MCSF Einstellungen für die Start-Layout verwenden, empfohlen dringend, dass Sie in einer LayoutModification.xml vollständig nutzen der Erfahrung Start wechseln. Beachten Sie außerdem, dass nicht alle Einstellungen vorhandene MCSF starten in Windows 10 unterstützt werden.

In dieser exemplarischen Vorgehensweise werden folgende Themen erläutert:

-   Erstellen Sie zwei Versionen des Layouts starten, eine Vorlage mit einem Ordner und ein weiteres ohne einen Ordner.

-   Konfigurieren von Einstellungen Layout MCSF starten, um festzulegen, dass wir die neue Layout Änderung XML für unsere Layout verwenden Varianten in der Datei CAF erstellen und Angeben der Start-Layouts betrifft die Varianten uns erstellten.

**Hinweis**  Stellen Sie sicher, dass Sie [Starten Layout für 10 für Windows mobile-Editionen](https://msdn.microsoft.com/library/windows/hardware/mt171093) gelesen haben vor dem Ausführen dieser exemplarischen Vorgehensweise. Das Thema enthält weitere detaillierte Informationen über die einzelnen Elemente in LayoutModification.xml, die nicht in dieser exemplarischen Vorgehensweise als auch Nachteile fallen und Einschränkungen, denen Sie berücksichtigen müssen.

 

**So konfigurieren Sie die Start-Layoutdatei Änderung**

1.  Erstellen Sie eine Datei namens LayoutModification1.xml.

2.  Fügen Sie XML-Code hinzu:

    -   Heften Sie eine Kachel mittlerer Größe in Zeile 6, Spalte 0 an. Die Kachel ist für die MSN News-app.
    -   PIN-Nummer einer mittleren Kachel in Zeile 6, Spalte 2. Die Kachel ist ein Weblink für die Contoso-Homepage.
    -   Anheften eines kleinen Ordners in Zeile 6, Spalte 4. Der Name des Ordners ist "Contoso apps", und enthält Folgendes:
        -   Eine mittlere Kachel für die app MSN Apps.
        -   Eine mittlere Kachel für die MSN Money-app.

    Das folgende XML-Beispiel zeigt, Sie müssen die Datei LayoutModification.xml hinzufügen.

    ```XML
    <?xml version="1.0" encoding="utf-8"?>
    <LayoutModificationTemplate
        xmlns="http://schemas.microsoft.com/Start/2014/LayoutModification"
        xmlns:defaultlayout="http://schemas.microsoft.com/Start/2014/FullDefaultLayout"
        xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout"
        Version="1">
        <DefaultLayoutOverride>
          <StartLayoutCollection>
                <defaultlayout:StartLayout>
                  <start:Group>
                      <start:Tile
                        AppUserModelID="Microsoft.BingNews_8wekyb3d8bbwe!ApplicationID"
                        Size="2x2"
                        Row="6"
                        Column="0"/>
                      <start:SecondaryTile
                        AppUserModelID="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge"
                        TileID="MyWeblinkTile"
                        Arguments="http://www.contoso.com"
                        DisplayName="Contoso Homepage"
                        Square150x150LogoUri="ms-appx:///Assets/MicrosoftEdgeSquare150x150.png" 
                        Wide310x150LogoUri="ms-appx:///Assets/MicrosoftEdgeWide310x150.png"
                        ShowNameOnSquare150x150Logo="true"
                        ShowNameOnWide310x150Logo="false"
                        BackgroundColor="#FF112233"
                        Size="2x2"
                        Row="6"
                        Column="2"/>
                      <start:Folder
                        Name="Contoso apps"
                        Size="2x2"
                        Row="6"
                        Column="4">
                        <start:Tile
                          AppUserModelID="Microsoft.BingMaps_8wekyb3d8bbwe!ApplicationID"
                          Size="2x2"
                          Row="0"
                          Column="0"/>
                        <start:Tile
                          AppUserModelID="Microsoft.BingFinance_8wekyb3d8bbwe!ApplicationID"
                          Size="2x2"
                          Row="0"
                          Column="2"/>
                        <!-- Remove these comments if you have an app that you can preload and want to add to the folder
                        <start:Tile
                          AppUserModelID="TBD"
                          Size="2x2"
                          Row="0"
                          Column="4"/>
                        -->
                      </start:Folder>
                  </start:Group>
                </defaultlayout:StartLayout>
          </StartLayoutCollection>
        </DefaultLayoutOverride>
    </LayoutModificationTemplate>
    ```

3.  Speichern Sie die XML-Datei, und notieren Sie den Speicherort der Datei; beispielsweise *C:\\Contoso\\Anpassungen\\LayoutModification1.xml*.

4.  Verwenden die gleiche XML-Datei, jetzt speichern sie als *LayoutModification2.xml*.

5.  Ändern Sie den Inhalt der neuen *LayoutModification2.xml* -Datei, indem Sie alles innerhalb der **Start: Folder** -Element löschen und ersetzen diese Ordnerspeicherort Kachel mit der MSN Money-app.

    Der Inhalt der XML-Datei sollte wie folgt aussehen:

    ```XML
    <?xml version="1.0" encoding="utf-8"?>
    <LayoutModificationTemplate
        xmlns="http://schemas.microsoft.com/Start/2014/LayoutModification"
        xmlns:defaultlayout="http://schemas.microsoft.com/Start/2014/FullDefaultLayout"
        xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout"
        Version="1">
        <DefaultLayoutOverride>
          <StartLayoutCollection>
                <defaultlayout:StartLayout>
                  <start:Group>
                      <start:Tile
                        AppUserModelID="Microsoft.BingNews_8wekyb3d8bbwe!ApplicationID"
                        Size="2x2"
                        Row="6"
                        Column="0"/>
                      <start:SecondaryTile
                        AppUserModelID="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge"
                        TileID="MyWeblinkTile"
                        Arguments="http://www.contoso.com"
                        DisplayName="Contoso Homepage"
                        Square150x150LogoUri="ms-appx:///Assets/MicrosoftEdgeSquare150x150.png" 
                        Wide310x150LogoUri="ms-appx:///Assets/MicrosoftEdgeWide310x150.png"
                        ShowNameOnSquare150x150Logo="true"
                        ShowNameOnWide310x150Logo="false"
                        BackgroundColor="#FF112233"
                        Size="2x2"
                        Row="6"
                        Column="2"/>
                      <start:Tile
                        AppUserModelID="Microsoft.BingFinance_8wekyb3d8bbwe!ApplicationID"
                        Size="2x2"
                        Row="6"
                        Column="4"/>
                  </start:Group>
                </defaultlayout:StartLayout>
          </StartLayoutCollection>
        </DefaultLayoutOverride>
    </LayoutModificationTemplate>
    ```

6.  Speichern der Xml-Datei, und notieren Sie den Speicherort der Datei. beispielsweise *C:\\Contoso\\Anpassungen\\LayoutModification2.xml*.

7.  Fügen Sie die Layout Änderung Dateien hinzu und konfigurieren Sie die Start-Layout-Einstellungen in die Antwortdatei MCSF CAF oder Windows-Bereitstellung (WPAF).

    -   MCSF: Finden Sie unter *Konfigurieren der Start-Layout* in [Configure Anpassung Settings](configure-customization-settings.md).
    -   Windows-Bereitstellung: Wenn Sie die Windows Imaging und Konfiguration Designer (ICD) Benutzeroberfläche verwenden, finden Sie unter *Konfigurieren der Start-Layout* verwendet [Die Windows-ICD-Benutzeroberfläche zum Anpassen und Erstellen einer mobilen Bild](use-the-windows-icd-ui-to-customize-and-build-a-mobile-image.md). Wenn Sie die Windows-ICD CLI (Hybridmethode) verwenden, finden Sie unter *Konfigurieren der Start-Layout* verwendet [Die Windows ICD CLI anpassen und Erstellen einer mobilen Bild](use-the-windows-icd-cli-to-customize-and-build-a-mobile-image.md).

 

 



