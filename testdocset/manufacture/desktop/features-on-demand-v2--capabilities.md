---
author: Justinha
Description: "Features auf Anforderung v2 (Funktionen), in Windows 10 eingeführt wurde, sind Windows-Feature-Pakete, die zu einem beliebigen Zeitpunkt hinzugefügt werden können. Allgemeine Features enthalten Sprachressourcen wie handschrifterkennung oder .NET Framework (. NetFx3)."
ms.assetid: 6390f427-a201-487e-928f-964e7b84327c
MSHAttr: PreferredLib:/library/windows/hardware
title: "Features für Demand V2 (Funktionen)"
ms.openlocfilehash: cef6ea515039e9f87c53cc2df4219f99b07daebe
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="features-on-demand-v2-capabilities"></a>Features für Demand V2 (Funktionen)


Features auf Anforderung v2 (Funktionen), in Windows 10 eingeführt wurde, sind Windows-Feature-Pakete, die zu einem beliebigen Zeitpunkt hinzugefügt werden können. Allgemeine Features enthalten Sprachressourcen wie handschrifterkennung oder .NET Framework (. NetFx3).

Bei der PC ein neues Feature benötigt, können sie das Feature Packs von Windows Update anfordern.

Im Gegensatz zu früheren Feature Packs Features bei Bedarf V2 auf mehrere Windows-Builds angewendet werden können, und können mithilfe von DISM ohne die Buildnummer hinzugefügt werden. Verwenden Sie immer Features bei Bedarf, die die Architektur des Betriebssystems entsprechen. Hinzufügen von Features bei Bedarf der falschen Architektur möglicherweise nicht sofort einen Fehler, aber wird wahrscheinlich Funktionalität Probleme in das Betriebssystem. 

## <a name="span-idaddingorremovingfeaturescapabilitiesspanspan-idaddingorremovingfeaturescapabilitiesspanspan-idaddingorremovingfeaturescapabilitiesspanadding-or-removing-featurescapabilities"></a><span id="Adding_or_removing_features_capabilities"></span><span id="adding_or_removing_features_capabilities"></span><span id="ADDING_OR_REMOVING_FEATURES_CAPABILITIES"></span>Hinzufügen und Entfernen von Features-Funktionen


Verwenden von DISM zum Hinzufügen oder Entfernen von Funktionen:

-   Verwenden Sie die/Online Option aus, um die Funktion an den PC hinzufügen.

-   Verwenden Sie/Image:&lt;Bereitstellungspfad&gt; Option, um die Möglichkeit, eine Windows-Abbilddatei (WIM) hinzufügen.
 

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Befehl</th>
<th align="left">Beschreibung</th>
<th align="left">Beispiel</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">/ Add-Funktion</td>
<td align="left"><p>Fügt eine Funktion zu einem Bild.</p>
<p>Für Pakete mit Abhängigkeiten zieht dies auch abhängige Pakete. Angenommen, wenn Sie das Paket Sprache hinzufügen, erhalten auch die Sprachsynthese und grundlegende Pakete neben Speech Sie.</p></td>
<td align="left">DISM.exe/Online /Add-Capability /CapabilityName:Language.Basic~\~\~En-US ~ 0.0.1.0</td>
</tr>
<tr class="even">
<td align="left">/ Get-Funktionen</td>
<td align="left">Profitieren Sie von Funktionen im Bild.</td>
<td align="left">DISM / Online /Get-Capabilities</td>
</tr>
<tr class="odd">
<td align="left">/ Get-CapabilityInfo</td>
<td align="left">Abrufen von Informationen von einer Funktion im Bild.</td>
<td align="left">DISM/Online /Get-CapabilityInfo /CapabilityName:Language.Basic~\~\~En-US ~ 0.0.1.0</td>
</tr>
<tr class="even">
<td align="left">/ Remove-Funktion</td>
<td align="left"><p>Entfernt eine Funktion aus einem Bild.</p>
<p>Hinweis: Eine Funktion, der andere Pakete abhängig sind, kann nicht entfernt werden. Wenn Sie die französische Handschrift und grundlegender Funktionen installiert haben, können nicht Sie beispielsweise die grundlegende Funktion entfernen. Dies schlägt fehl.</p></td>
<td align="left">DISM.exe / Online /Remove-Capability /CapabilityName:Language.Basic~~~en-US~0.0.1.0</td>
</tr>
</tbody>
</table>

 

## <a name="span-idcapabilitiesreferencespanspan-idcapabilitiesreferencespanspan-idcapabilitiesreferencespancapabilities-reference"></a><span id="Capabilities_reference"></span><span id="capabilities_reference"></span><span id="CAPABILITIES_REFERENCE"></span>Funktionen (engl.)


### <a name="net-framework"></a>.NET framework  

| Komponente | Beschreibung                                                             |
|-----------|-------------------------------------------------------------------------|
| NetFx3    | .NET Framework ein viele Clientanwendungen erforderliche Softwareframework 3.x. |

 

### <a name="language-capabilities"></a>Sprachfunktionen

Nicht alle Funktionen stehen für jede Sprache.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Komponente</th>
<th align="left">Beispiel-Dateiname</th>
<th align="left">Dependencies</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Standard</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-Basic-fr-fr-Package</code></td>
<td align="left">Keine</td>
<td align="left"><p>Rechtschreibprüfung, Textvorhersage, Wortumbruch und Silbentrennung Wenn für die Sprache zur Verfügung.</p>
<p>Sie müssen diese Komponente vor dem Hinzufügen der folgenden Komponenten hinzufügen.</p></td>
</tr>
<tr class="even">
<td align="left">Schriftarten</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-Fonts-Thai-Package</code></td>
<td align="left">Keine</td>
<td align="left"><p>Schriftarten.</p>
<p>Erforderlich für einige Regionen zum Rendern von Text, der in Dokumenten angezeigt wird. Beispielsweise ten-ten erfordert das Schriftart Thai Pack. </p></td>
</tr>
<tr class="odd">
<td align="left">Optische zeichenerkennung</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-OCR-fr-fr-Package</code></td>
<td align="left">Standard</td>
<td align="left">Erkennt und Text in einem Bild ausgegeben.</td>
</tr>
<tr class="even">
<td align="left">Handschrifterkennung</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-Handwriting-fr-fr-Package</code></td>
<td align="left">Standard</td>
<td align="left">Ermöglicht die handschrifterkennung für Geräte mit Input Stift.</td>
</tr>
<tr class="odd">
<td align="left">Text-Sprach-</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-TextToSpeech-fr-fr-Package</code></td>
<td align="left">Standard</td>
<td align="left">Text zu Sprachein-und-Ausgabe, von Cortana und Sprachausgabe verwendet werden können.</td>
</tr>
<tr class="even">
<td align="left">Spracherkennung</td>
<td align="left"><code>Microsoft-Windows-LanguageFeatures-Speech-fr-fr-Package</code></td>
<td align="left">Grundlegende, Sprache</td>
<td align="left">VoIP erkennt Eingaben, von Cortana und Windows-Spracherkennung verwendet werden.</td>
</tr>
</tbody>
</table>

### <a name="font-capabilities"></a>Schriftartfunktionen

Beim Hinzufügen von Sprachen für einige Regionen, müssen Sie die Schriftartfunktionen hinzufügen.

| Region      | Beschreibung                            | Erforderliche Schriftart-Funktion                              |
|-------------|----------------------------------------|-------------------------------------------------------|
| Uhr ET       | Amharisch                                | Microsoft-Windows-LanguageFeatures-Fonts-Ethi-Package |
| Ar-SA       | Arabisch (Saudi-Arabien)                  | Microsoft-Windows-LanguageFeatures-Fonts-Arab-Package |
| Ar SY       | Arabisch (Syrien)                         | Microsoft-Windows-LanguageFeatures-Fonts-Syrc-Package |
| wie IN       | Assamesisch                               | Microsoft-Windows-LanguageFeatures-Fonts-Beng-Package |
| Bn BD       | Bangla (Bangladesch)                    | Microsoft-Windows-LanguageFeatures-Fonts-Beng-Package |
| Bn-IN       | Bangla (Indien)                         | Microsoft-Windows-LanguageFeatures-Fonts-Beng-Package |
| Chr-Cher-US | Cherokee (Cherokee)                    | Microsoft-Windows-LanguageFeatures-Fonts-Cher-Package |
| Anlagen-IR       | Persisch                                | Microsoft-Windows-LanguageFeatures-Fonts-Arab-Package |
| gu-IN       | Gujarati                               | Microsoft-Windows-LanguageFeatures-Fonts-Gujr-Package |
| IE-IL       | Hebräisch                                 | Microsoft-Windows-LanguageFeatures-Fonts-Hebr-Package |
| hi-IN       | Hindi                                  | Microsoft-Windows-LanguageFeatures-Fonts-Deva-Package |
| ja-JP       | Japanisch                               | Microsoft-Windows-LanguageFeatures-Fonts-Jpan-Package |
| km KH       | Khmer                                  | Microsoft-Windows-LanguageFeatures-Fonts-Khmr-Package |
| KN-IN       | Kannada                                | Microsoft-Windows-LanguageFeatures-Fonts-Knda-Package |
| Kok-IN      | Konkani                                | Microsoft-Windows-LanguageFeatures-Fonts-Deva-Package |
| Ko-KR       | Koreanisch                                 | Microsoft-Windows-LanguageFeatures-Fonts-Kore-Package |
| Ku-Arabische-IQ  | Zentrale Kurdisch (Arabisch)               | Microsoft-Windows-LanguageFeatures-Fonts-Arab-Package |
| lo LA       | Laotisch                                    | Microsoft-Windows-LanguageFeatures-Fonts-Laoo-Package |
| ml-IN       | Malayalam                              | Microsoft-Windows-LanguageFeatures-Fonts-Mlym-Package |
| Mr-IN       | Marathi                                | Microsoft-Windows-LanguageFeatures-Fonts-Deva-Package |
| Ne NP       | Nepali                                 | Microsoft-Windows-LanguageFeatures-Fonts-Deva-Package |
| oder-IN       | Odia                                   | Microsoft-Windows-LanguageFeatures-Fonts-Orya-Package |
| PA-Arabische-PK  | Punjabi (Arabisch)                       | Microsoft-Windows-LanguageFeatures-Fonts-Arab-Package |
| PA-IN       | Punjabi                                | Microsoft-Windows-LanguageFeatures-Fonts-Guru-Package |
| Prs-AF      | Dari                                   | Microsoft-Windows-LanguageFeatures-Fonts-Arab-Package |
| SD-Arabische-PS  | Sindhi (Arabisch)                        | Microsoft-Windows-LanguageFeatures-Fonts-Arab-Package |
| SI-LK       | Sinhala                                | Microsoft-Windows-LanguageFeatures-Fonts-Sinh-Package |
| SYR SY      | Syrisch                                 | Microsoft-Windows-LanguageFeatures-Fonts-Syrc-Package |
| TA-IN       | Tamil                                  | Microsoft-Windows-LanguageFeatures-Fonts-Taml-Package |
| Te-IN       | Telugu                                 | Microsoft-Windows-LanguageFeatures-Fonts-Telu-Package |
| ten-ten       | Thailändisch                                   | Microsoft-Windows-LanguageFeatures-Fonts-Thai-Package |
| Ti-ET       | Tigrinya                               | Microsoft-Windows-LanguageFeatures-Fonts-Ethi-Package |
| UG-CN       | Uigurisch                                 | Microsoft-Windows-LanguageFeatures-Fonts-Arab-Package |
| Your PK       | Urdu                                   | Microsoft-Windows-LanguageFeatures-Fonts-Arab-Package |
| Zh-CN       | Chinesisch (vereinfacht)                   | Microsoft-Windows-LanguageFeatures-Fonts-Hans-Package |
| Zh-HK       | Chinesisch (traditionell, Hongkong (SAR)) | Microsoft-Windows-LanguageFeatures-Fonts-Hant-Package |
| Zh-TW       | Chinesisch (traditionell, Taiwan)          | Microsoft-Windows-LanguageFeatures-Fonts-Hant-Package |

### <a name="additional-fonts-available"></a>Weitere Schriftarten zur Verfügung:

Diese Schriften sind optional und für jede Region nicht erforderlich.

| Name                                                                          | Beschreibung                                                                                                                                         |
|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| Microsoft-Windows-LanguageFeatures-Fonts-PanEuropeanSupplementalFonts-Package | Pan-Europa zusätzliche Schriftarten. Enthält zusätzliche Schriftarten: Arial Nova, Georgia Pro, Gill Sans Nova, Neue Haas Grotesk, Rockwell Nova, Verdana Pro. |

### <a name="other-region-specific-requirements"></a>Sonstige Anforderungen regionsspezifische

| Region | Beschreibung                   | Funktion                                             | Beschreibung                                                                                                            |
|--------|-------------------------------|--------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Zh-TW  | Chinesisch (traditionell, Taiwan) | Microsoft-Windows-InternationalFeatures-Taiwan-Paket | Ergänzende Unterstützung für Taiwan Datum Formatierung Anforderungen. Paket wird Kunden in Taiwan bereitgestellt werden. |

### <a name="list-of-all-language-related-features-on-demand"></a>Liste aller sprachbezogenen Features bei Bedarf
[Laden Sie die Liste aller verfügbaren Sprache FODs](http://download.microsoft.com/download/8/3/0/830AC3A9-68CF-4F10-9357-F27E0A03148A/Windows 10 1607 FOD to LP Mapping Table.xlsx)

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen

[Hinzufügen von Language Packs zu Windows](add-language-packs-to-windows.md)

[DISM Funktionen Packen Befehlszeilenoptionen zum Warten](dism-capabilities-package-servicing-command-line-options.md)

