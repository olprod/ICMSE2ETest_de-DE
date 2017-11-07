---
author: Justinha
Description: Funktionsweise von Oobe.xml
ms.assetid: 6df5c611-96f3-4268-9208-8455aa293954
MSHAttr: PreferredLib:/library/windows/hardware
title: Funktionsweise von Oobe.xml
ms.openlocfilehash: 2c1bf500400e3dc2e0932bd37c60abe7e1a1e0cb
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="how-oobexml-works"></a>Funktionsweise von Oobe.xml


**Oobe.XML** ist eine Content-Datei, die können Text und Bilder organisieren und angeben und Voreinstellungen für die Anpassung der zuerst auftreten. Mehrere **Oobe.xml** Dateien können für Sprache und Region-spezifische Lizenzbedingungen und Einstellungen, damit Benutzer entsprechenden Informationen angezeigt, sobald sie ihren PCs teilnehmen beginnen. Durch Angeben von Informationen in der Datei **Oobe.xml** , leiten OEMs Benutzer nur die wichtigsten Aufgaben ausführen, die erforderlich sind, um ihren PCs teilnehmen einzurichten.

Windows überprüft und lädt **Oobe.xml** an den folgenden Speicherorten, in der folgenden Reihenfolge:

1.  **%Windir%\\System32\\Oobe\\Info\\"Oobe.xml"**

2.  **%Windir%\\System32\\Oobe\\Info\\Standard\\Oobe.xml**

3.  **%Windir%\\System32\\Oobe\\Info\\Standard\\**&lt;*Sprache*&gt;\\**"Oobe.xml"**

4.  **%Windir%\\System32\\Oobe\\Info\\***Land/Region*&gt;**\\Oobe.xml**

5.  **%Windir%\\System32\\Oobe\\Info\\***Land/Region*&gt;\\&lt;*Sprache*&gt;\\**Oobe.xml**

Wenn Sie Anpassungen, die alle Länder/Regionen und Sprachen umfassen verfügen, können die Dateien Oobe.xml Speicherort 1 platziert werden.

Wenn Sie eine einzige Region und Sprache System ausgeliefert werden, die benutzerdefinierte Datei **Oobe.xml** platziert werden soll die \\Info (Speicherort 1) oder \\Standardverzeichnis (Position 2). Diese Standorte sind funktional gleichwertig.

Wenn Sie haben den Protokollversand an mehrere Länder/Regionen und Einstelllungen OOBE Anpassungen für einzelne Länder/Regionen, jeweils mit einer einzigen Sprache erfordern, sollten alle **Oobe.xml** Dateien in Speicherorte 4 und 5 platziert werden.

Wenn Sie den Protokollversand an mehrere Länder/Regionen mit mehreren Sprachen sind, gelten die folgenden Richtlinien:

-   Platzieren Sie Land/Region-spezifische Informationen im Speicherort 4.

-   Speicherort 5 versehen Sie Sprachspezifische Informationen für jedes jeweiligen Land/Region.

## <a name="span-idsingle-languagedeploymentsspanspan-idsingle-languagedeploymentsspanspan-idsingle-languagedeploymentsspansingle-language-deployments"></a><span id="Single-language_deployments"></span><span id="single-language_deployments"></span><span id="SINGLE-LANGUAGE_DEPLOYMENTS"></span>Single-Sprache-Bereitstellungen


Wenn Sie zu einem Land/Region in einer einzigen Sprache Bereitstellung PCs von, platzieren Sie einzelne **Oobe.xml** -Datei in ** \\%windir%\\System32\\Oobe\\Info**. Diese Datei enthält alle Ihre Anpassungen für die erste Windows-Funktionen.

Beispielsweise kann eine englische Version von Windows, die in den USA übermittelt werden die folgenden Verzeichnisstruktur aufweisen:

**\\%Windir%\\System32\\Oobe\\Info\\Oobe.xml**

Wenn Sie PCs, um mehrere Land/Region in einer einzigen Sprache liefern sind und Planen Sie Ihre Anpassungen an unterschiedlichen Standorten variieren, speichern Sie eine Datei **Oobe.xml** in ** \\%windir%\\System32\\Oobe\\Info.**

Diese Datei kann die Standardeinstellungen für regionale enthalten, die für dem Benutzer angezeigt werden soll. Sie sollten einen Standardsatz Anpassungen, auch für den Fall, dass der Benutzer eine Land/Region auswählt, die Sie für bestimmte Anpassungen vorgenommen noch nicht enthalten. Die Datei **Oobe.xml** sollte auch enthalten die &lt; *"eulafilename"* &gt; Knoten mit dem Namen der angepassten Lizenzbedingungen, die Sie verwenden möchten.

Speichern Sie eine Datei **Oobe.xml** bezüglich der jedes Land/Region, die eindeutige enthält Inhalte in ** \\%windir%\\System32\\**&lt;*Land/Region, die Sie zum Bereitstellen*&gt;\\&lt;*Sprache, die Sie in bereitstellen*&gt;. Nachdem der Benutzer eine Land/Region sich entschieden hat, werden diese Dateien verwendet, zusätzliche erforderliche Anpassungen vor angezeigt.

Beispielsweise eine englische Version von Windows übermittelt, in den USA und Kanada kann die folgende Verzeichnisstruktur aufweisen:

** \\%Windir%\\System32\\Oobe\\Info\\Oobe.xml** (EULA Dateinamen und regionale Einstellungen)

** \\% WINDIR% % System32\\Oobe\\Info\\244\\1033\\Oobe.xml** (Benutzerdefinierte Inhalte für Vereinigte Staaten)

**\\%Windir%\\System32\\Oobe\\Info\\39\\1033\\Oobe.xml (benutzerdefinierte Inhalte für Kanada)**

## <a name="span-idmultiple-languageorregiondeploymentsspanspan-idmultiple-languageorregiondeploymentsspanspan-idmultiple-languageorregiondeploymentsspanmultiple-language-or-region-deployments"></a><span id="Multiple-language_or_region_deployments"></span><span id="multiple-language_or_region_deployments"></span><span id="MULTIPLE-LANGUAGE_OR_REGION_DEPLOYMENTS"></span>Mehrsprachige oder einer Region Bereitstellungen


Wenn Sie die Bereitstellung von PCs sind für eine oder mehrere Länder/Regionen und bieten PCs unter Windows durch zusätzliche Language Packs, speichern Sie eine Datei **Oobe.xml** in ** \\%windir%\\System32\\Oobe\\Info**. Diese Datei kann die Standardeinstellungen für regionale enthalten, die Sie für dem Benutzer anzeigen möchten. Sie sollten einen Standardsatz Anpassungen, auch für den Fall, dass der Benutzer eine Land/Region auswählt, die Sie für bestimmte Anpassungen vorgenommen noch nicht enthalten. Diese **Oobe.xml** sollte auch enthalten die &lt; *"eulafilename"* &gt; Knoten mit dem Namen der benutzerdefinierten Lizenzbedingungen, die Sie verwenden möchten.

Speichern Sie eine Datei **Oobe.xml** bezüglich der jedes Land/Region, die eindeutige enthält Inhalte in \\%windir%\\System32\\&lt;*Land/Region, die Sie zum Bereitstellen*&gt;\\&lt;*Sprache, die Sie in bereitstellen*&gt;. Nachdem der Benutzer eine Land/Region sich entschieden hat, wird diese Datei zusätzliche erforderliche Anpassungen vor anzuzeigen.

Beispielsweise würde eine englische Version von Windows, die in den USA und Kanada ausgeliefert wird die folgende Verzeichnisstruktur verwenden:

** \\%Windir%\\System32\\Oobe\\Info\\Oobe.xml** (Logo, EULA Dateinamen und regionale Einstellungen)

** \\%Windir%\\System32\\Oobe\\Info\\244\\1033\\Oobe.xml** (Benutzerdefinierte Inhalte für Vereinigte Staaten)

\\%Windir%\\System32\\Oobe\\Info\\39\\1033\\**Oobe.xml** (benutzerdefinierte Inhalte für Kanada)

Wenn Sie die Bereitstellung von PCs sind für eine oder mehrere Länder/Regionen und PCs unter Windows durch zusätzliche Language Packs liefern, speichern Sie eine Datei **Oobe.xml** im ** \\%windir%\\System32\\Oobe\\Info**. Diese Datei **Oobe.xml** enthalten sollte die * &lt;"eulafilename"&gt; * Knoten mit dem Namen des benutzerdefinierten EULA, die Sie verwenden möchten.

Platzieren eines **Oobe.xml** für jede Windows-Sprache, die Sie in einschließlich sind ** \\%windir%\\System32\\Standard\\**&lt;*Sprache, die Sie in bereitstellen*&gt;. Diese Dateien sollten die regionale Standardeinstellungen enthalten, die Sie für eine bestimmte Sprache als auch eine Reihe von Anpassungen, anzeigen möchten, für den Fall, dass der Benutzer eine Land/Region auswählt, die Sie für bestimmte Anpassungen erstellt haben.

Speichern Sie eine Datei **Oobe.xml** bezüglich der jedes Land/Region, die enthält Inhalte in ** \\%windir%\\System32\\***Land/Region, die Sie zum Bereitstellen*&gt;\\&lt;*Sprache, die Sie in bereitstellen*&gt;. Nachdem der Benutzer eine Land/Region ausgewählt, dient diese Datei zum Anzeigen Ihrer zusätzliche erforderliche Anpassungen vor.

Beispielsweise würde eine Version von Windows mit Englisch als auch Französisch Sprachpakete, die in den USA und Kanada ausgeliefert wird die folgende Verzeichnisstruktur verwenden:

-   Logo und Endbenutzer-LIZENZVERTRAG:

    ** \\%Windir%\\System32\\Oobe\\Info\\Oobe.xml** (Logo und Dateinamen EULA)

-   Regionale Einstellungen und Fallback für Inhalte, die für bestimmte Lands/der Region nicht lokalisiert wurde:

    ** \\%Windir%\\System32\\Oobe\\Info\\Standard\\1033\\Oobe.xml** (Standardeinstellung regionale Einstellungen und englischen Inhalt der Benutzer entscheidet sich Land/Region nicht den USA oder Kanada)

    ** \\%Windir%\\System32\\Oobe\\Info\\Standard\\1036\\Oobe.xml** (Standardeinstellung regionale Einstellungen "und" Französisch Inhalt der Benutzer entscheidet sich Land/Region als USA oder Kanada)

-   Land oder Region-spezifische Inhalte in den entsprechenden Sprachen

    ** \\%Windir%\\System32\\Oobe\\Info\\244\\1033\\Oobe.xml** (Benutzerdefinierte Inhalte für die USA auf Englisch)

    ** \\%Windir%\\System32\\Oobe\\Info\\244\\1036\\Oobe.xml** (Benutzerdefinierte Inhalte für die USA auf Französisch)

    ** \\%Windir%\\System32\\Oobe\\Info\\39\\1033\\Oobe.xml** (Benutzerdefinierte Inhalte in Englisch Kanada)

    ** \\%Windir%\\System32\\Oobe\\Info\\39\\1036\\Oobe.xml** (Benutzerdefinierte Inhalte in Französisch Kanada)

### <a name="span-idcountryregionfolderformatspanspan-idcountryregionfolderformatspanspan-idcountryregionfolderformatspancountryregion-folder-format"></a><span id="Country_region_folder_format"></span><span id="country_region_folder_format"></span><span id="COUNTRY_REGION_FOLDER_FORMAT"></span>Format der Land/region

So identifizieren Sie die Land/region

1.  Suchen Sie nach der Land/Region GeoID Bezeichner verwenden die [Tabelle geografischen Standorten](http://go.microsoft.com/fwlink/?LinkId=131360) auf **MSDN**. Diese Werte werden in Hexadezimalzahl angezeigt.

2.  Konvertieren Sie des Werts von hexadezimalen Decimal, und verwenden Sie diesen Wert für den Namen des Ordners. Beispielsweise um einen Ordner für Chile (GeoID 0x2E) zu erstellen, nennen Sie den Ordner "46" an.

    ``` syntax
    \%WINDIR%\System32\Oobe\Info\46\Oobe.xml
    ```

### <a name="span-idlanguagefolderformatspanspan-idlanguagefolderformatspanspan-idlanguagefolderformatspanlanguage-folder-format"></a><span id="Language_folder_format"></span><span id="language_folder_format"></span><span id="LANGUAGE_FOLDER_FORMAT"></span>Format der Sprachordner

Um die Sprache zu identifizieren, verwenden Sie die decimal Version des Werts Gebietsschema-ID (LCID). Beispielsweise um einen Spanisch Ordner erstellen, nennen Sie den Ordner "3082" an.

``` syntax
%WINDIR%\System32\Oobe\Info\Default\3082\Oobe.xml
```

Es gibt viele weitere LCIDs als Sprachen. Wenige LCIDs entsprechen den Sprachen, die in Windows freigegeben werden können. Weitere Informationen dazu, welche Sprachen mit Windows, auf welcher Ebene und deren Dezimal-IDs veröffentlichten finden Sie unter [Verfügbare Language Packs](http://go.microsoft.com/fwlink/?LinkId=206620) auf **TechNet**.

 

 





