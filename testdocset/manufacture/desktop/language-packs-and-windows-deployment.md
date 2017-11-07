---
author: Justinha
Description: Language Packs
ms.assetid: 051a9952-c160-4f51-8575-bde6e4868b03
MSHAttr: PreferredLib:/library/windows/hardware
title: Language Packs
ms.openlocfilehash: e52f6ea346fd5c160282b9bafa3ea2b38bffd498
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="language-packs"></a>Language Packs 


Um PCs entwerfen, die für Kunden in unterschiedlichen Regionen besser geeignet, können Sie mit dem richtigen Satz von lokalen Sprachen, Einstellungen, und Tastaturen oder andere Eingabegeräte Windows einrichten.

## <a name="span-idwhatsnewwithlanguagepacksforwindows10spanspan-idwhatsnewwithlanguagepacksforwindows10spanspan-idwhatsnewwithlanguagepacksforwindows10spanwhats-new-with-language-packs-for-windows-10"></a><span id="What_s_new_with_Language_Packs_for_Windows_10_"></span><span id="what_s_new_with_language_packs_for_windows_10_"></span><span id="WHAT_S_NEW_WITH_LANGUAGE_PACKS_FOR_WINDOWS_10_"></span>Was ist neu bei Language Packs für Windows 10?


Um die Größe des Bilds reduzieren, haben Sprachpakete jetzt in die folgenden Sprachkomponenten aufgeteilt wurde und [Features auf Anforderung V2 (Funktionen)](features-on-demand-v2--capabilities.md):

-   Benutzeroberflächentext (Language Pack CAB-Datei)
-   Grundlegende (Rechtschreibprüfung, Eingabe)
-   Schriftarten
-   Handschrift
-   Optische zeichenerkennung
-   Text-Sprach-
-   Spracherkennung
-   Retail Demo Erfahrung

Sie können nun wählen, Ihr Bild nur Core Language Pack Benutzeroberflächenressourcen hinzugefügt Bildgröße reduziert.

Um Cortana Features Vorinstallation, fügen Sie die folgenden Features bei Bedarf: Benutzeroberflächentext, die Basic, Sprachsynthese und die Language-Komponenten. 

Nicht alle Komponenten und Features bei Bedarf stehen für jede Sprache.

Weitere Informationen finden Sie unter [Hinzufügen von Language Packs mit Windows](add-language-packs-to-windows.md).

## <a name="span-idlanguagepacksforwindowsspanspan-idlanguagepacksforwindowsspanspan-idlanguagepacksforwindowsspanlanguage-packs-for-windows"></a><span id="Language_packs_for_Windows"></span><span id="language_packs_for_windows"></span><span id="LANGUAGE_PACKS_FOR_WINDOWS"></span>Sprachpakete für Windows


Sprachpakete enthalten den Text für die Dialogfelder, Menüelemente und Helpfiles an, denen die in Fenstern angezeigt.

Für einige Regionen können von Benutzeroberflächen-Sprachpaketen (Benutzeroberflächen-Sprachpaketen) zusätzliche Übersetzungen sind für die Dialogfelder großem Maß genutzt, Menüelemente und Helpfile Inhalte bereitstellen. Benutzeroberflächen-Sprachpaketen basieren auf ein übergeordnetes Language Pack um den Rest des Inhalts bereitzustellen.

### <a name="span-idgetlanguagepacksandlipsspanspan-idgetlanguagepacksandlipsspanspan-idgetlanguagepacksandlipsspanget-language-packs-and-lips"></a><span id="Get_language_packs_and_LIPs"></span><span id="get_language_packs_and_lips"></span><span id="GET_LANGUAGE_PACKS_AND_LIPS"></span>Abrufen von Language Packs und Benutzeroberflächen-Sprachpaketen

-   OEMs und System-Builder mit Microsoft-Software-Lizenzbedingungen können Language Packs und Benutzeroberflächen-Sprachpaketen von der [Microsoft OEM-Website](http://go.microsoft.com/fwlink/?LinkId=131359) oder der [OEM Partner Center](http://go.microsoft.com/fwlink/?LinkId=131358)herunterladen.
-   IT-Experten können Sprachpakete von der [Microsoft Volume Licensing Website](http://go.microsoft.com/fwlink/?LinkId=125893)herunterladen.
-   Nach der Installation von Windows Endbenutzer herunterladen und installieren Sie zusätzliche Language Packs in den **Einstellungen**können > **Uhrzeit- und Sprache** > **Regions- und spracheinstellungen** > **Hinzufügen einer Sprache**. 

Verwandte Informationen:

-   [Verfügbare Sprachpakete für Windows](available-language-packs-for-windows.md). Listet alle unterstützten Language Packs und Benutzeroberflächen-Sprachpaketen für mehrere Versionen von Windows und die ID-Codes.

### <a name="span-idaddlanguagestowindowsspanspan-idaddlanguagestowindowsspanspan-idaddlanguagestowindowsspanadd-languages-to-windows"></a><span id="Add_languages_to_Windows"></span><span id="add_languages_to_windows"></span><span id="ADD_LANGUAGES_TO_WINDOWS"></span>Hinzufügen von Sprachen zu Windows

Wenn Sie mehr als eine Sprache oder eine LIP Windows einschließen, werden Ihre Kunden können die Sprache auswählen, die ihren Anforderungen während Windows OOBE am besten erfüllt.

Es gibt verschiedene Methoden zum Installieren von Language Packs:

-   Sie können ein Language Pack Windows hinzufügen, mit dem Befehlszeilentool **Dism/Add-Package** . Finden Sie unter [Hinzufügen und Entfernen von Language Packs auf einem ausgeführten Windows-Installation](add-and-remove-language-packs-on-a-running-windows-installation.md) oder [Hinzufügen und Entfernen von Sprachpaketen Offline mithilfe von DISM](add-and-remove-language-packs-offline-using-dism.md).
-   Zum Bereitstellen einer mehrsprachigen Version von Windows mithilfe von Windows Setup (beispielsweise ein Unternehmen Windows-DVD-Abbild oder ein Satz von Bildern in einem Unternehmensnetzwerk verfügbar) können Sie das Installationsprogramm Sprachressourcen hinzufügen. Finden Sie unter [Hinzufügen von Support in mehreren Sprachen auf einem Windows-Verteilung](add-multilingual-support-to-a-windows-distribution.md).

    Für Unternehmen bereitgestellten oder Netzwerk-basierte Installationen müssen Sie möglicherweise auch die Windows-Vorinstallation Environment (Windows PE) zu aktualisieren, die Benutzer sehen, wenn sie wie und wo auswählen, Windows auf dem Computer zu installieren. Weitere Informationen finden Sie unter [Windows PE: Bereitstellen und Anpassen von](winpe-mount-and-customize.md).

-   Nach der Installation von Windows können Endbenutzer herunterladen und installieren zusätzliche Language Packs und Benutzeroberflächen-Sprachpaketen aus der **Language** -Systemsteuerung. Weitere Informationen finden Sie in die [Lokale Sprache-Programm](http://go.microsoft.com/fwlink/?LinkId=262343).

## <a name="span-idlanguagepacksforrecoverytoolsspanspan-idlanguagepacksforrecoverytoolsspanspan-idlanguagepacksforrecoverytoolsspanlanguage-packs-for-recovery-tools"></a><span id="Language_packs_for_recovery_tools"></span><span id="language_packs_for_recovery_tools"></span><span id="LANGUAGE_PACKS_FOR_RECOVERY_TOOLS"></span>Language Packs für Wiederherstellungstools


Wenn Dinge falsche wechseln, können Windows Recovery Environment (Windows RE) erleichtern das System und die Daten wiederherstellen. Wenn Sie die verfügbaren Sprachen für Windows aktualisieren, aktualisieren die verfügbaren Sprachen in die Wiederherstellungstools: [Windows RE anpassen](customize-windows-re.md).

## <a name="span-idpreparekeyboardstimezonesandotherregionalsettingsspanspan-idpreparekeyboardstimezonesandotherregionalsettingsspanspan-idpreparekeyboardstimezonesandotherregionalsettingsspanprepare-keyboards-time-zones-and-other-regional-settings"></a><span id="Prepare_keyboards__time_zones__and_other_regional_settings_"></span><span id="prepare_keyboards__time_zones__and_other_regional_settings_"></span><span id="PREPARE_KEYBOARDS__TIME_ZONES__AND_OTHER_REGIONAL_SETTINGS_"></span>Vorbereiten von Tastaturen, Zeitzonen und anderen regionalen Einstellungen


Sie können den Standard-Tastaturlayout, Sprache und Gebietsschema, angeben, während der Bereitstellung oder nach der Installation von Windows.

-   [Konfigurieren von internationalen Einstellungen in Windows](configure-international-settings-in-windows.md)
-   [Input Standardprofile (Input Gebietsschemata) in Windows](default-input-locales-for-windows-language-packs.md): Liste der input Standardprofile (Sprache und Tastatur-Paare) für jede Region verwendet.
-   [Standard-Zeitzonen](default-time-zones.md): Listet die Standardzeitzone für jede Region verwendet.
-   [Tastatur-IDs für Windows](windows-language-pack-default-values.md): Listet die Tastatur Hexadezimalwerte beim Konfigurieren von Eingabe-Profile verwendet.

## <a name="span-idlanguagesforappsspanspan-idlanguagesforappsspanspan-idlanguagesforappsspanlanguages-for-apps"></a><span id="Languages_for_apps"></span><span id="languages_for_apps"></span><span id="LANGUAGES_FOR_APPS"></span>Sprachen für apps


Viele apps enthalten mehrere Sprachen unterstützt, obwohl einige erfordern separate Installation der Sprachpakete ordnungsgemäß funktioniert. Wenden Sie sich an den Entwickler app.

Installieren Sie alle Ihre Sprachen auf Windows im Allgemeinen vor der Installation von apps. Dadurch wird sichergestellt, dass die Sprachressourcendateien für jede verfügbare apps zur Verfügung stehen.

Weitere Informationen finden Sie unter [Multilingual User Interface (Windows)](http://go.microsoft.com/fwlink/p/?LinkId=698642).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Hinzufügen von Language Packs zu Windows](add-language-packs-to-windows.md)

[Features für Demand V2 (Funktionen)](features-on-demand-v2--capabilities.md)

 

 






