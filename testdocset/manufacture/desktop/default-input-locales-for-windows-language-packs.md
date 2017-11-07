---
author: Justinha
Description: "Eingabe-Profile (oder Eingabe) beschreiben die Sprache für die Eingabe und der Tastatur, auf der sie eingegeben wird. Wenn der erste Benutzer, Windows anmeldet und ihre Region identifiziert, wird Windows die input Profile."
ms.assetid: 0bae00b5-dfcb-472e-a271-07ef62ad5fc5
MSHAttr: PreferredLib:/library/windows/hardware
title: Standardeingabe Profiles (Input Gebietsschemata) in Windows
ms.openlocfilehash: 33fbe882b810cc8d7fbc45ffd68e105cbcd5dfb8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="default-input-profiles-input-locales-in-windows"></a>Standardeingabe Profiles (Input Gebietsschemata) in Windows


Eingabe-Profile (oder Eingabe) beschreiben die Sprache für die Eingabe und der Tastatur, auf der sie eingegeben wird. Beim erste Benutzer meldet sich in Windows und ihre Region identifiziert, wird Windows Eingabe-Profile.

Die Eingabe-Profile bestehen aus einer [Sprach-ID](http://go.microsoft.com/fwlink/?LinkId=63026) und einen [Tastatur-ID](windows-language-pack-default-values.md). Beispielsweise Arabisch (algerisch fest) input Profils ist 1401:00020401, wobei 1401 hexadezimaler Bezeichner der Sprache: Arabisch (Algerien) und 00020401 ist der hexadezimale Bezeichner der Tastatur: 101 Arabisch.

Wenn der Benutzer zuerst das Datum und Uhrzeit-Format (Benutzergebietsschema) als Algerien identifiziert, Windows sowohl das primäre input Profil richtet und eine sekundäre Profil Eingaben: Französisch (Frankreich) mit französischen Tastatur. Das sekundäre input Profil kann den Benutzer durch die Bereitstellung einer Tastatur mit einer lateinischen Zeichensatz für Aufgaben, die sie, wie Ausfüllen von e-Mail-Adressen erfordern helfen. Einige Zeichensätze (wie CHS IME) enthalten einen lateinischen Zeichensatz integrierten.

Windows verwendet die Sprachkomponente des Eingangs Profils für Aufgaben wie Rechtschreibprüfung, Silbentrennung und Text Vorhersage des den beabsichtigten Tastendruck, bei Verwendung die Touchscreen-Tastatur.

Beim Einrichten von neue Geräte für Ihre Benutzer können die Befehle DISM: /Set-InputLocale oder Standardsprache identifiziert eine standardmäßige Eingabefokus Profil. Sie können entweder das input Profil durch das Sprach- und Paar (1401:00020401) auswählen oder eine Sprache können\\Region Tag ein, um die Standardeinstellungen für diese Sprache/Region empfangen.

Beispiele:

``` syntax
Dism /image:C:\test\offline /Set-InputLocale:042d:0000040a
Dism /image:C:\test\offline /Set-InputLocale:0411:{03B5835F-F03C-411B-9CE2-AA23E1171E36}{A76C93D9-5523-4E90-AAFA-4DB112F9AC76}
Dism /image:C:\test\offline /Set-InputLocale:id-ID
Dism /image:C:\test\offline /Set-AllIntl:fr-FR
```

Eine Liste der Namen der Sprache/Kultur ist finden Sie unter [Verfügbaren Language Packs für Windows](available-language-packs-for-windows.md).

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Sprache/Region</th>
<th align="left">Primäre input Profil (Sprache und Tastatur Paar)</th>
<th align="left">Sekundäre input-Profil</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Afrikaans - Südafrika</p></td>
<td align="left"><p>Assured Forwarding ZA: USA - Englisch (0436:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Albanisch - Albanien</p></td>
<td align="left"><p>SQL-AL: Albanisch (041c: 0000041c)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Elsässisch – Frankreich</p></td>
<td align="left"><p>Gsw-FR: Französisch (0484:0000040 c)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Amharisch - Äthiopien</p></td>
<td align="left"><p>Uhr ET: Amharisch Eingabemethode (045e: {E429B25A-E5D3-4D1F-9BE3-0C608477E3A1}{8F96574E-C86C-4bd6-9666-3F7327D4CBE8})</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Arabisch - Algerien</p></td>
<td align="left"><p>Ar-DZ: Arabisch (102) AZERTY (1401:00020401)</p></td>
<td align="left"><p>fr-FR: Französisch (040c: 0000040c)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Arabisch - Bahrain</p></td>
<td align="left"><p>Ar BH: Arabisch (101) (3c 01:00000401)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Arabisch - Ägypten</p></td>
<td align="left"><p>Ar-EG: Arabisch (101) (0c 01:00000401)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Arabisch - Irak</p></td>
<td align="left"><p>Ar IQ: Arabisch (101) (0801:00000401)</p></td>
<td align="left"><p>En-US: United States - English (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Arabisch - Jordanien</p></td>
<td align="left"><p>Ar-JO: Arabisch (101) (2c 01:00000401)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Arabisch - Kuwait</p></td>
<td align="left"><p>Ar KW: Arabisch (101) (3401:00000401)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Arabisch - Libanon</p></td>
<td align="left"><p>Ar kg: Arabisch (101) (3001:00000401)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Arabisch - Libyen</p></td>
<td align="left"><p>Ar Übernehmen: Arabisch (101) (1001:00000401)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Arabisch - Marokko</p></td>
<td align="left"><p>Ar-MA: Arabisch (102) AZERTY (1801:00020401)</p></td>
<td align="left"><p>fr-FR: Französisch (040c: 0000040c)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Arabisch - Oman</p></td>
<td align="left"><p>Ar OM: Arabisch (101) (2001:00000401)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Arabisch - Katar</p></td>
<td align="left"><p>Ar QA: Arabisch (101) (4001:00000401)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Arabisch – Saudi-Arabien</p></td>
<td align="left"><p>Ar-SA: Arabisch (101) (0401:00000401)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Arabisch – Saudi-Arabien</p></td>
<td align="left"><p>Ar SY: Arabisch (101) (2801:00000401)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Arabisch - Tunesien</p></td>
<td align="left"><p>Ar TN: Arabisch (102) AZERTY (1c 01:00020401)</p></td>
<td align="left"><p>fr-FR: Französisch (040c: 0000040c)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Arabisch - Vereinigte Arabische Emirate</p></td>
<td align="left"><p>Ar AE: Arabisch (101) (3801:00000401)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Arabisch - Jemen</p></td>
<td align="left"><p>Ar-IHRE: Arabisch (101) (2401:00000401)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Armenisch - Armenien</p></td>
<td align="left"><p>Hy Uhr: Armenisch Phonetic (042b:0002042b)</p></td>
<td align="left"><p>Hy Uhr: Armenisch Schreibmaschine (042b:0003042b)</p>
<p>ru-RU: Russisch (0419:00000419)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Assamesisch - Indien</p></td>
<td align="left"><p>als IN: Assamesisch - Inscript (044d: 0000044d)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Aserbaidschanisch - Aserbaidschan (Kyrillisch)</p></td>
<td align="left"><p>az-Cyrl-AZ: Aserbaidschan Kyrillisch (082c: 0000082c)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p>
<p>az-Latn-AZ: Aserbaidschanisch (Lateinisch) (042c: 0000042c)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Aserbaidschanisch - Aserbaidschan (Lateinisch)</p></td>
<td align="left"><p>az-Latn-AZ: Aserbaidschan Lateinisch (042c: 0000042c)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p>
<p>az-Cyrl-AZ: Aserbaidschanisch Kyrillisch (082c: 0000082c)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Bangla (Bangladesch)</p></td>
<td align="left"><p>Bn BD: Bangla - Bangladesch (0845:00000445)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Bangla - Indien (Bengali-Schrift)</p></td>
<td align="left"><p>Bn-IN: Bangla Indien-INSCRIPT (0445:00020445)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Baschkirisch - Russische Föderation</p></td>
<td align="left"><p>BA-RU: Baschkirisch (046d: 0000046d)</p></td>
<td align="left"><p>ru-RU Russisch (0419:00000419)</p>
<p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Baskisch - Baskisch</p></td>
<td align="left"><p>EU-ES: Spanisch (042d:0000040a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Weißrussisch - Weißrussland</p></td>
<td align="left"><p>werden NACH dem: Weißrussisch (0423:00000423)</p></td>
<td align="left"><p>ru-RU: Russisch (0419:00000419)</p>
<p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Bosnisch - Bosnien und Herzegowina (Kyrillisch)</p></td>
<td align="left"><p>BS-Cyrl-BA: Bosnisch (Kyrillisch) (201a:0000201a)</p></td>
<td align="left"><p>BS-Latn-BA: Kroatisch (141a:0000041a)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Bosnisch - Bosnien und Herzegowina (Lateinisch)</p></td>
<td align="left"><p>BS-Latn-BA: Kroatisch (141a:0000041a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Bretonischen - Frankreich</p></td>
<td align="left"><p>Br-FR: Französisch (047e:0000040 c)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Bulgarisch - Bulgarien</p></td>
<td align="left"><p>bg-BG: Bulgarisch (0402:00030402)</p></td>
<td align="left"><p>En-US: USA - International (0409:00020409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Birmanisch - Myanmar</p></td>
<td align="left"><p>Meine MM: Myanmar (0455:00010 c 00)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Katalanisch - Katalanisch</p></td>
<td align="left"><p>CA-ES: Spanisch (0403:0000040a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Zentrale Atlas Tamazight (Lateinisch) - Algerien</p></td>
<td align="left"><p>fr-FR: Französisch (040c: 0000040c)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Zentrale Atlas Tamazight (Lateinisch) - Algerien</p></td>
<td align="left"><p>Tzm-Latn-DZ: zentralen Atlas Tamazight (085f:0000085f)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Zentrale Atlas Tamazight (Tifinagh) - Marokko</p></td>
<td align="left"><p>Tzm-Tfng-MA: (105f:0000105f)</p></td>
<td align="left"><p>fr-FR: Französisch (040c: 0000040c)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Zentrale Kurdisch (Irak)</p></td>
<td align="left"><p>Ku-Arabische-IQ: (0492:00000492)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Cherokee (Cherokee, Vereinigte Staaten)</p></td>
<td align="left"><p>Chr-Cher-US: Cherokee-Staat (045c: 0000045c)</p></td>
<td align="left"><p>Cherokee-Staat phonetischen (045c: 0001045c)</p>
<p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Chinesisch - VR CHINA</p></td>
<td align="left"><p>Zh-CN: Microsoft Pinyin - einfache Fast (0804: {81D4E9C9-1D3B-41BC-9E6C-4B40BF79E35E}{FA550B04-5AD7-411f-A5AC-CA038EC515D7})</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Chinesisch – Taiwan</p></td>
<td align="left"><p>Zh-TW: Chinesisch (traditionell) - neue phonetischen (0404: {B115690A-EA02-48D5-A231-E3578D2FDF80}{B2F9C502-1742-11D4-9790-0080C882687E})</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Korsisch - Frankreich</p></td>
<td align="left"><p>Co-FR: Französisch (0483:0000040 c)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Kroatisch - Bosnien und Herzegowina</p></td>
<td align="left"><p>HR-BA: Kroatisch (101a:0000041a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Kroatisch - Kroatien</p></td>
<td align="left"><p>hr-HR: Kroatisch (041a:0000041a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Tschechisch - Tschechische Republik</p></td>
<td align="left"><p>Cs-CZ: Tschechisch (0405:00000405)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dänisch - Dänemark</p></td>
<td align="left"><p>da-DK: Dänisch (0406:00000406)</p></td>
<td align="left"><p>En-US: Dänisch (0409:00000406)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Dari - Afghanistan</p></td>
<td align="left"><p>Prs AF: Persisch (Standard) (048c: 00050429)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Divehi - Malediven</p></td>
<td align="left"><p>DV Metaverse: Divehi Phonetic (0465:00000465)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Niederländisch - Belgien</p></td>
<td align="left"><p>NL-SEIN: Belgien (Punkt) (0813:00000813)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Niederländisch - Niederlande</p></td>
<td align="left"><p>NL-NL: USA - International (0413:00020409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Dzongkha</p></td>
<td align="left"><p>DZ BT: 0C 51: 00000C 51;: 0409: 00000409</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Englisch – Australien</p></td>
<td align="left"><p>En-AU: USA - Englisch (0c 09:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Englisch – Belize</p></td>
<td align="left"><p>En-BZ: USA - Englisch (2809:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Englisch - Kanada</p></td>
<td align="left"><p>En-CA: USA - Englisch (1009:00000409)</p></td>
<td align="left"><p>En-CA: Kanadische mehrsprachigen Standard (1009:00011009)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Englisch – Karibik</p></td>
<td align="left"><p>En-029: USA - Englisch (2409:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Englisch – Indien</p></td>
<td align="left"><p>En-IN: Indien (4009:00004009)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Englisch – Irland</p></td>
<td align="left"><p>En-IE: Irisch (1809:00001809)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Englisch – Jamaika</p></td>
<td align="left"><p>En-JM: USA - Englisch (2009:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Englisch – Malaysia</p></td>
<td align="left"><p>En-MEINE: USA - Englisch (4409:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Englisch - Neuseeland</p></td>
<td align="left"><p>En-NZ: USA - Englisch (1409:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Englisch - Philippinen</p></td>
<td align="left"><p>En-PH: USA - Englisch (3409:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Englisch – Singapur</p></td>
<td align="left"><p>En-SG: USA - Englisch (4809:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Englisch - Südafrika</p></td>
<td align="left"><p>En-ZA: United States - English (1c 09:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Englisch - Trinidad</p></td>
<td align="left"><p>En-TT: United States - English (2c 09:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Englisch – Großbritannien</p></td>
<td align="left"><p>En-GB: Großbritannien (0809:00000809)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Englisch - Vereinigte Staaten</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Englisch – Simbabwe</p></td>
<td align="left"><p>En-ZW: USA - Englisch (3009:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Estnisch - Estland</p></td>
<td align="left"><p>et EE: Estnisch (0425:00000425)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Färöisch - Färöer</p></td>
<td align="left"><p>Fo FO: Dänisch (0438:00000406)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Filipino - Philippinen</p></td>
<td align="left"><p>Datei PH: United States - English (0464:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Finnisch - Finnland</p></td>
<td align="left"><p>Fi-FI: Finnisch (040b:0000040b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Französisch – Belgien</p></td>
<td align="left"><p>FR-SEIN: Französisch (Belgien) (080c: 0000080c)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Französisch – Kanada</p></td>
<td align="left"><p>fr-CA: Kanadische mehrsprachigen Standard (0c0c:00011009)</p></td>
<td align="left"><p>En-CA: Kanadische mehrsprachigen Standard (1009:00011009)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Französisch – Frankreich</p></td>
<td align="left"><p>fr-FR: Französisch (040c: 0000040c)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Französisch – Luxemburg</p></td>
<td align="left"><p>FR-LU: Französisch (Schweiz) (140c: 0000100C)</p></td>
<td align="left"><p>FR-LU: Französisch (140c: 0000040c)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Französisch – Monaco</p></td>
<td align="left"><p>FR-MC: Französisch (180c: 0000040c)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Französisch – Schweiz</p></td>
<td align="left"><p>FR-Kapitel: Französisch (Schweiz) (100c: 0000100c)</p></td>
<td align="left"><p>de-Kapitel: Deutsch (Schweiz) (0807:00000807)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Friesisch - Niederlande</p></td>
<td align="left"><p>GJ-NL: USA - International (0462:00020409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Fulah (Lateinisch, Senegal)</p></td>
<td align="left"><p>FF-Latn-SN: Wolof (0867:00000488)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Galizisch - Galizisch</p></td>
<td align="left"><p>-ES GL: Spanisch (0456:0000040a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Georgisch - Georgien</p></td>
<td align="left"><p>KA GE: Georgisch (QWERTY) (0437:00010437)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Deutsch - Österreich</p></td>
<td align="left"><p>de-AT: Deutsch (0c 07:00000407)</p></td>
<td align="left"><p>de-AT: (Deutsch)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Deutsch – Deutschland</p></td>
<td align="left"><p>de-DE: Deutsch (0407:00000407)</p></td>
<td align="left"><p>de-DE: (Deutsch)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Deutsch - Liechtenstein</p></td>
<td align="left"><p>de-LI: Deutsch (Schweiz) (1407:00000807)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Deutsch - Luxemburg</p></td>
<td align="left"><p>de LU: Deutsch (1007:00000407)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Deutsch - Schweiz</p></td>
<td align="left"><p>de-Kapitel: Deutsch (Schweiz) (0807:00000807)</p></td>
<td align="left"><p>FR-Kapitel: Schweiz Französisch (100C: 0000100 C)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Griechisch - Griechenland</p></td>
<td align="left"><p>El g: Griechisch (0408:00000408)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Grönländisch - Grönland</p></td>
<td align="left"><p>KL GL: Dänisch (046f:00000406)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Guarani - Paraguay</p></td>
<td align="left"><p>gn Hierhin: Guarani (0474:00000474)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Gujarati - Indien (Gujarati-Skript)</p></td>
<td align="left"><p>gu-IN: Gujarati (0447:00000447)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Hausa (Lateinisch) - Nigeria</p></td>
<td align="left"><p>HA-Latn-NG: Haussa (0468:00000468)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Hawaiianisch - Vereinigte Staaten</p></td>
<td align="left"><p>Haw-US: (0475:00000475)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Hebräisch – Israel</p></td>
<td align="left"><p>IE-IL: (040 d: 0002040d)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Hindi - Indien</p></td>
<td align="left"><p>hi-IN: Hindi traditionell (0439:00010439)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Ungarisch - Ungarn</p></td>
<td align="left"><p>Hu-HU: Ungarisch (040e:0000040e)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Isländisch - Island</p></td>
<td align="left"><p>ist-IST: Isländisch (040f:0000040f)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Igbo - Nigeria</p></td>
<td align="left"><p>Ig NG: Igbo (0470:00000470)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Inarisamisch - Finnland</p></td>
<td align="left"><p>smn-FI: Finnisch mit Samisch (243b:0001083b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Indonesisch - Indonesien</p></td>
<td align="left"><p>ID-ID: USA - Englisch (0421:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Inuktitut (Lateinisch) - Kanada</p></td>
<td align="left"><p>IE-Latn-CA: Inuktitut - Lateinisch (085 d: 0000085d)</p></td>
<td align="left"><p>En-CA: USA - Englisch (1009:00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Inuktitut (Silbenschrift) - Kanada</p></td>
<td align="left"><p>IE-Dosen-CA: Inuktitut - Naqittaut (045 d: 0001045d)</p></td>
<td align="left"><p>En-CA: USA - Englisch (1009:00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Irisch - Irland</p></td>
<td align="left"><p>GA IE: Irisch (083c: 00001809)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Xhosa / Xhosa - Südafrika</p></td>
<td align="left"><p>Xh-ZA: United States - English (0434:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Zulu / Zulu - Südafrika</p></td>
<td align="left"><p>zu-ZA: USA - Englisch (0435:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Italienisch – Italien</p></td>
<td align="left"><p>IT-IT: Italienisch (0410:00000410)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Italienisch - Schweiz</p></td>
<td align="left"><p>IT-Kapitel: Französisch (Schweiz) (0810:0000100-c)</p></td>
<td align="left"><p>IT-Kapitel: Italienisch (0810:00000410)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Japanisch – Japan</p></td>
<td align="left"><p>ja-JP: Microsoft IME (0411: {03B5835F-F03C-411B-9CE2-AA23E1171E36}{A76C93D9-5523-4E90-AAFA-4DB112F9AC76})</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Javanese (Lateinisch) - Indonesien</p></td>
<td align="left"><p>JV-Latn-ID: US (00 0c: 00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Kannada - Indien (Kannada-Skript)</p></td>
<td align="left"><p>KN-IN: Kannada (044b:0000044b)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Kasachisch - Kasachstan</p></td>
<td align="left"><p>KK KZ: Kasachisch (043f:0000043f)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Khmer - Kambodscha</p></td>
<td align="left"><p>km KH: Khmer (0453:00000453)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>K ' iche - Guatemala</p></td>
<td align="left"><p>Qut-GT: Lateinamerika (0486:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Kinyarwanda - Ruanda</p></td>
<td align="left"><p>Lese-LESE: USA - Englisch (0487:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Konkani - Indien</p></td>
<td align="left"><p>Kok-IN: Devanagari-INSCRIPT (0457:00000439)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Koreanisch (Extended Wansung) - Korea</p></td>
<td align="left"><p>Ko-KR: Microsoft IME (0412: {A028AE76-01B1-46C2-99C4-ACD9858AE02F}{B5FE1F02-D5F2-4445-9C03-C568F23C99A1})</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Kirgisisch - Kirgisistan</p></td>
<td align="left"><p>KY KG: Kirgisisch Kyrillisch (0440:00000440)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Laotisch - Demokratische Volksrepublik LAOS</p></td>
<td align="left"><p>lo LA: Laotisch (0454:00000454)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Lettisch - Legacy</p></td>
<td align="left"><p>LV LV: Lettisch (QWERTY) (0426:00010426)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Lettisch - Standard</p></td>
<td align="left"><p>LV LV: Lettisch (Standard) (0426:00020426)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Litauisch - Litauen</p></td>
<td align="left"><p>Lt-LT: Litauisch (0427:00010427)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Niedersorbisch - Deutschland</p></td>
<td align="left"><p>SBG angenommene DE: Sorbisch Standard (082e:0002042e)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Lule-Sami - Norwegen</p></td>
<td align="left"><p>Smj-NR.: Norwegisch mit Samisch (103b:0000043b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Lule-Sami - Schweden</p></td>
<td align="left"><p>Smj SE: Schwedisch mit Samisch (143b:0000083b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Lëtzebuergisch - Luxemburg</p></td>
<td align="left"><p>kg LU: Lëtzebuergisch (046e:0000046e)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Mazedonisch - F.Y.R.O.M</p></td>
<td align="left"><p>MK MK: Mazedonien (FYROM) - Standard (042f:0001042f)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Malaiisch - Brunei</p></td>
<td align="left"><p>MS-BN: United States - English (083e:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Malaiisch - Malaysia</p></td>
<td align="left"><p>MS-MEINE: USA - Englisch (043e:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Malayalam - Indien (Malayalam-Schrift)</p></td>
<td align="left"><p>ml-IN: Malayalam (044c: 0000044c)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Maltesisch - Malta</p></td>
<td align="left"><p>MT MT: Maltesisch 47-Tasten (043a:0000043a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Maori - Neuseeland</p></td>
<td align="left"><p>Mi NZ: Maori (0481:00000481)</p></td>
<td align="left"><p>En-NZ: USA - Englisch (1409:00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Mapudungun - Chile</p></td>
<td align="left"><p>Arn-CL: Lateinamerika (047a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Marathi - Indien</p></td>
<td align="left"><p>Mr-IN: Marathi (044e:0000044e)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Mohawk - Kanada</p></td>
<td align="left"><p>MOH enthalten-CA: USA - Englisch (047c: 00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Mongolisch (Kyrillisch) - Mongolei</p></td>
<td align="left"><p>Mn MN: Mongolisch Kyrillisch (0450:00000450)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Mongolisch (Mongolisch) - Mongolei</p></td>
<td align="left"><p>Mn-Mong-MN: traditionelles Mongolisch (Standard) (0c 50:00010850)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Mongolisch (Mongolisch – PRC-Legacy)</p></td>
<td align="left"><p>Mn-Mong-CN: Mongolisch (Mongolisch Skript) (0850:00000850)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Mongolisch (Mongolisch – VR CHINA – Standard)</p></td>
<td align="left"><p>Mn-Mong-CN: Mongolisch (Mongolisch Skript) (0850:00010850)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>N'ko – Guinea</p></td>
<td align="left"><p>Nqo-GN: N'Ko (0c 00 00: 00090C)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Nepali - Federal Demokratische Republik der Nepalesische</p></td>
<td align="left"><p>Ne NP: Nepali (0461:00000461)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Nordsamisch - Finnland</p></td>
<td align="left"><p>SE-FI: Finnisch mit Samisch (0c3b:0001083b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Nordsamisch - Norwegen</p></td>
<td align="left"><p>SE NO: Norwegisch mit Samisch (043b:0000043b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Nordsamisch - Schweden</p></td>
<td align="left"><p>SE SE: Schwedisch mit Samisch (083b:0000083b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Norwegisch - Norwegen (Bokmål)</p></td>
<td align="left"><p>nb-NO: Norwegisch (0414:00000414)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Norwegisch - Norwegen (Nynorsk)</p></td>
<td align="left"><p>Nn NO: Norwegisch (0814:00000414)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Okzitanisch - Frankreich</p></td>
<td align="left"><p>oC-FR: Französisch (0482:0000040 c)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Odia - Indien (Odia Schrift)</p></td>
<td align="left"><p>oder-IN: Odia (0448:00000448)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Paschto - Afghanistan</p></td>
<td align="left"><p>PS-AF: Paschto (Afghanistan) (0463:00000463)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Persisch</p></td>
<td align="left"><p>Anlagen-IR: Zentraladministration Kurdisch (0429:00000429)</p></td>
<td align="left"><p>Anlagen-IR: Persisch (Standard) (0429:00050429)</p>
<p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Polnisch - Polen</p></td>
<td align="left"><p>PL-PL: Polnisch (0415:00000415)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Portugiesisch – Brasilien</p></td>
<td align="left"><p>pt-BR: Portugiesisch (Brasilien ABNT) (0416:00000416)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Portugiesisch - Portugal</p></td>
<td align="left"><p>pt-PT: Portugiesisch (0816:00000816)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Punjabi - Indien (Gurmukhi-Skript)</p></td>
<td align="left"><p>PA-IN: Punjabi (0446:00000446)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Punjabi (Islamische Republik Pakistan)</p></td>
<td align="left"><p>PA-Arabische-PK: Urdu (0846:00000420)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Quechua - Bolivien</p></td>
<td align="left"><p>Quz-FELD: Lateinamerika (046b:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Quechua - Ecuador</p></td>
<td align="left"><p>Quz EG: Lateinamerika (086b:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Quechua - Peru</p></td>
<td align="left"><p>Quz PE: Lateinamerika (0c6b:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Rumänisch - Rumänien</p></td>
<td align="left"><p>RO-RO: Rumänisch (Standard) (0418:00010418)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Rätoromanisch - Schweiz</p></td>
<td align="left"><p>RM-Kapitel: Deutsch (Schweiz) (0417:00000807)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Russisch - Russische Föderation</p></td>
<td align="left"><p>ru-RU: Russisch (0419:00000419)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Sakha - Russland</p></td>
<td align="left"><p>Sah-RU: Sakha (0485:00000485)</p></td>
<td align="left"><p>ru-RU Russisch (0419:00000419)</p>
<p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Sanskrit - Indien</p></td>
<td align="left"><p>SA-IN: Devanagari-INSCRIPT (044f:00000439)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Schottisches Gälisch – Großbritannien</p></td>
<td align="left"><p>GD GB: Gälisch (0491:00011809)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Serbisch - Bosnien und Herzegowina (Kyrillisch)</p></td>
<td align="left"><p>SR-Cyrl-BA: Serbisch (Kyrillisch) (1c1a:00000c1a)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Serbisch - Bosnien und Herzegowina (Lateinisch)</p></td>
<td align="left"><p>SR-Latn-BA: Serbisch (Lateinisch) (181a:0000081a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Serbisch – Montenegro (Kyrillisch)</p></td>
<td align="left"><p>SR-Cyrl-ME: Serbisch (Kyrillisch) (301a:00000c1a)</p></td>
<td align="left"><p>En-US: USA - International (0409:00020409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Serbisch – Montenegro (Lateinisch)</p></td>
<td align="left"><p>SR-Latn-ME: Serbisch (Lateinisch) (2c1a:0000081a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Serbisch – Serbien (Kyrillisch)</p></td>
<td align="left"><p>SR-Cyrl-RS: Serbisch (Kyrillisch) (281a:00000c1a)</p></td>
<td align="left"><p>En-US: USA - International (0409:00020409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Serbisch – Serbien (Lateinisch)</p></td>
<td align="left"><p>SR-Latn-RS: Serbisch (Lateinisch) (241a:0000081a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Serbisch – Serbien und Montenegro (früher) (Kyrillisch)</p></td>
<td align="left"><p>SR-Cyrl-CS: Serbisch (Kyrillisch) (0c1a:00000c1a)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Serbisch – Serbien und Montenegro (früher) (Lateinisch)</p></td>
<td align="left"><p>SR-Latn-CS: Serbisch (Lateinisch) (081a:0000081a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Sesotho sa Leboa / Nord Sotho - Südafrika</p></td>
<td align="left"><p>Nso-ZA: Sesotho sa Leboa (046c: 0000046c)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Tsuana / Tswana - Botsuana</p></td>
<td align="left"><p>TN BW: Tsuana (0832:00000432)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Tsuana / Tswana - Südafrika</p></td>
<td align="left"><p>TN ZA: Tsuana (0432:00000432)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Shona – Simbabwe</p></td>
<td align="left"><p>Sn-Latn-ZW: US (00 0c: 00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Sindhi (Islamische Republik Pakistan)</p></td>
<td align="left"><p>SD-Arabische-PK: Urdu (0859:00000420)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Sinhala - Bangladesch</p></td>
<td align="left"><p>SI-LK: Sinhala (045b:0000045b)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Skoltsamisch - Finnland</p></td>
<td align="left"><p>SMS-FI: Finnisch mit Samisch (203b:0001083b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Slowakisch - Slowakei</p></td>
<td align="left"><p>sk-SK: Slowakisch (041b:0000041b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Slowenisch - Slowenien</p></td>
<td align="left"><p>sl SI: Slowenisch (0424:00000424)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Südsamisch - Norwegen</p></td>
<td align="left"><p>SMA NO: Norwegisch mit Samisch (183b:0000043b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Südsamisch - Schweden</p></td>
<td align="left"><p>SMA SE: Schwedisch mit Samisch (1c3b:0000083b)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Spanisch - Argentinien</p></td>
<td align="left"><p>Es AR: Lateinamerika (2c0a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Spanisch - Bolivarische Republik Venezuela</p></td>
<td align="left"><p>Es-VE: Lateinamerika (200a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Spanisch - Bolivien</p></td>
<td align="left"><p>Es-FELD: Lateinamerika (400a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Spanisch - Chile</p></td>
<td align="left"><p>Es-CL: Lateinamerika (340a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Spanisch - Kolumbien</p></td>
<td align="left"><p>Es-CO: Lateinamerika (240a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Spanisch – Costa Rica</p></td>
<td align="left"><p>Es CR: Lateinamerika (140a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Spanisch – Dominikanische Republik</p></td>
<td align="left"><p>es: Lateinamerika (1c0a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Spanisch - Ecuador</p></td>
<td align="left"><p>Es EG: Lateinamerika (300a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Spanisch – El Salvador</p></td>
<td align="left"><p>Es PA: Lateinamerika (440a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Spanisch - Guatemala</p></td>
<td align="left"><p>Es-GT: Lateinamerika (100a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Spanisch - Honduras</p></td>
<td align="left"><p>Es HN: Lateinamerika (480a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Spanisch – Mexiko</p></td>
<td align="left"><p>es-MX: Lateinamerika (080a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Spanisch – Nicaragua</p></td>
<td align="left"><p>Es NI: Lateinamerika (4c0a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Spanisch – Panama</p></td>
<td align="left"><p>Es PA: Lateinamerika (180a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Spanisch - Paraguay</p></td>
<td align="left"><p>Es Hierhin: Lateinamerika (3c0a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Spanisch - Peru</p></td>
<td align="left"><p>Es PE: Lateinamerika (280a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Spanisch - Freistaat Puerto Rico</p></td>
<td align="left"><p>Es PR: Lateinamerika (500a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Spanisch - Spanien (internationale Sortierung)</p></td>
<td align="left"><p>es-ES: Spanisch (0c0a:0000040a)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Spanisch - Spanien (traditionell)</p></td>
<td align="left"><p>es-ES_tradnl: Spanisch (040a:0000040a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Spanisch - USA</p></td>
<td align="left"><p>es-US: Lateinamerika (540a:0000080a)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Spanisch - Uruguay</p></td>
<td align="left"><p>Es UY: Lateinamerika (380a:0000080a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Standard Marokko Tamazight - Marokko</p></td>
<td align="left"><p>Zgh-Tfng-MA: Tifinagh (Basic) (0c 00: 0000105F)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Suaheli - Kenia</p></td>
<td align="left"><p>SW-Schlüssel: USA - Englisch (0441:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Schwedisch - Finnland</p></td>
<td align="left"><p>Sv-FI: Schwedisch (081d: 0000041d)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Schwedisch - Schweden</p></td>
<td align="left"><p>SV-SE: Schwedisch (041d: 0000041d)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Syrisch - Syrien</p></td>
<td align="left"><p>SYR SY: Syrisch (045a:0000045a)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Tadschikisch - Tadschikistan</p></td>
<td align="left"><p>TG-Cyrl-TJ: Tadschikisch (0428:00000428)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Tamil - Indien</p></td>
<td align="left"><p>TA-IN: Tamilisch (0449:00000449)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Tamil - Bangladesch</p></td>
<td align="left"><p>TA-LK: Tamilisch (0849:00000449)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Tatarisch – Russland (Legacy)</p></td>
<td align="left"><p>TT-RU: Tatarisch (0444:00000444)</p></td>
<td align="left"><p>ru-RU: Russisch (0419:00000419)</p>
<p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Tatarisch – Russland (Standard)</p></td>
<td align="left"><p>TT-RU: Tatarisch (0444:00010444)</p></td>
<td align="left"><p>ru-RU: Russisch (0419:00000419)</p>
<p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Telugu - Indien (Telugu-Schrift)</p></td>
<td align="left"><p>Te-IN: Telugu (044a:0000044a)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Thai - Thailand</p></td>
<td align="left"><p>ten-ten: Thai Kedmanee (041e:0000041e)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Tibetisch - Volksrepublik CHINA</p></td>
<td align="left"><p>Feld-CN: Tibetisch (Volksrepublik CHINA) (0451:00010451)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Tigrinya (Eritrea)</p></td>
<td align="left"><p>Ti-ET: Tigrinya Eingabemethode (0473: {E429B25A-E5D3-4D1F-9BE3-0C608477E3A1}{3CAB88B7-CC3E-46A6-9765-B772AD7761FF})</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Tigrinya (Äthiopien)</p></td>
<td align="left"><p>Ti-ET: Tigrinya Eingabemethode (0473: {E429B25A-E5D3-4D1F-9BE3-0C608477E3A1}{3CAB88B7-CC3E-46A6-9765-B772AD7761FF})</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Türkisch - Türkei</p></td>
<td align="left"><p>tr-TR: Türkisch Q (041f:0000041f)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Turkmenisch - Turkmenistan</p></td>
<td align="left"><p>Tk TM: Turkmenisch (0442:00000442)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Ukrainisch - Ukraine</p></td>
<td align="left"><p>Großbritannien-UA: Ukrainisch (Erweitert) (0422:00020422)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Obersorbisch - Deutschland</p></td>
<td align="left"><p>HSB-DE: Sorbisch Standard (042e:0002042e)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Urdu – Indien</p></td>
<td align="left"><p>Your-IN: Urdu (0820:00000420)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Urdu (Islamische Republik Pakistan)</p></td>
<td align="left"><p>Your PK: Urdu (0420:00000420)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Uigurisch - VR CHINA</p></td>
<td align="left"><p>UG-CN: Uigurisch (0480:00010480)</p></td>
<td align="left"><p>En-US: United States - English (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Usbekisch - Usbekistan (Kyrillisch)</p></td>
<td align="left"><p>UZ-Cyrl-UZ: Usbekisch Kyrillisch (0843:00000843)</p></td>
<td align="left"><p>UZ-Latn-UZ: United States - English (0443:00000409)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Usbekisch - Usbekistan (Lateinisch)</p></td>
<td align="left"><p>UZ-Latn-UZ: United States - English (0443:00000409)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Valencian - Valencia</p></td>
<td align="left"><p>CA-ES-Valencia: Spanisch (0803:0000040a)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="odd">
<td align="left"><p>Vietnamesisch - Vietnam</p></td>
<td align="left"><p>vi-VN: Vietnamesisch (042a:0000042a)</p></td>
<td align="left"><p>En-US: USA - Englisch (: 0409: 00000409)</p></td>
</tr>
<tr class="even">
<td align="left"><p>Walisisch - Großbritannien</p></td>
<td align="left"><p>CY-GB: Großbritannien erweitert (0452:00000452)</p></td>
<td align="left"><p>En-GB: Großbritannien (0809:00000809)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Wolof - Senegal</p></td>
<td align="left"><p>Wo SN: Wolof (0488:00000488)</p></td>
<td align="left"><p></p></td>
</tr>
<tr class="even">
<td align="left"><p>Yi - Volksrepublik CHINA</p></td>
<td align="left"><p>II-CN: Yi Eingabe Method(0478:{E429B25A-E5D3-4D1F-9BE3-0C608477E3A1}{409C8376-007B-4357-AE8E-26316EE3FB0D})</p></td>
<td align="left"><p>Zh-CN: Microsoft Pinyin - einfache Fast (0804: {81D4E9C9-1D3B-41BC-9E6C-4B40BF79E35E}{FA550B04-5AD7-411f-A5AC-CA038EC515D7})</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Yoruba - Nigeria</p></td>
<td align="left"><p>yo NG: Yoruba (046a:0000046a)</p></td>
<td align="left"><p></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Standard-Zeitzonen](default-time-zones.md)

[Hinzufügen von Language Packs zu Windows](add-language-packs-to-windows.md)

[Verfügbare Sprachpakete für Windows](available-language-packs-for-windows.md)

[Tastatur-IDs für Windows](windows-language-pack-default-values.md)

[DISM Sprachen und International Befehlszeilenoptionen zum Warten](dism-languages-and-international-servicing-command-line-options.md)

 

 






