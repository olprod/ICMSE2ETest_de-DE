---
title: "Benutzerdefinierte Protokollierung mit Feld Sanitäter"
description: "Benutzerdefinierte Protokollierung mit Feld Sanitäter"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 762da1e5-abfe-4888-a886-8e74e7658362
ms.openlocfilehash: a3b7a23cf7ceb950ec4e346ec8dd966c45ef0bad
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="custom-logging-with-field-medic"></a>Benutzerdefinierte Protokollierung mit Feld Sanitäter


Sie können konfigurieren, Sanitäter zum Generieren von Berichten aus benutzerdefinierten Protokollierungsmodule zu, die nicht Teil der Standardgruppe von Protokollierungen sind dar. Um eine benutzerdefinierte Protokollierung anzugeben, erstellen Sie eine Profil-XML-Datei und kopieren Sie es auf Telefon\\Dokumente\\FieldMedic\\CustomProfiles.

Klicken Sie auf Gerät Entwicklung kann T-Shell XML-Dateien in den freigegebenen Ordner OEM platzieren verwendet werden. Ein einfaches Paket kann erstellt werden, um die Dateien dort hinzuzufügen. Weitere Informationen zur Struktur von XML, die eine benutzerdefiniertes Profil-XML-Datei enthalten, finden Sie unter [Authoring Aufzeichnung Profile](http://msdn.microsoft.com/library/windows/hardware/hh448223.aspx).

## <a name="create-a-custom-profile-xml-file"></a>Erstellen einer benutzerdefinierten XML-Profildatei


Es folgt ein Beispiel zum Erstellen einer benutzerdefinierten Profils-XML-Datei. Angenommen Sie, Sie möchten eine benutzerdefinierte Kategorie erstellen, die diese beiden ETW-Anbieter enthält.

| Name des ETW-Anbieters                          | ETW-Anbieter-GUID                    |
|--------------------------------------------|--------------------------------------|
| Microsoft-WindowsPhone-TileHelper          | B3448AD3-4BE8-4F7C-892B-EA1D69B14ADB |
| Microsoft-WindowsPhone-AccessoryManagerSvc | 68EC658D-C373-4166-996F-D8A757108B27 |

 

Diese benutzerdefinierte XML-Profildatei beschreibt eine Ereignissammlung, die eine ID EventCollector hat\_TileManager. Der Ereignissammlung enthält zwei Anbietern, die in angegeben werden die &lt;EventProvider&gt; und &lt;EventProviderId&gt; Elemente.

``` syntax
<?xml version="1.0" encoding="utf-8" standalone='yes'?>

<WindowsPerformanceRecorder Version="1.0" Author="You" Team="Your team" Comments="Your comments" Company="Your company" Copyright="Your company" Tag="WPDiet">
  <Profiles>
    <!-- Event Collectors -->
    <EventCollector Id="EventCollector_TileManager" Name="WPDiet TileHelper Category Event Collector" Private="false" ProcessPrivate="false" Secure="false" Realtime="false">
      <BufferSize Value="128"/>
      <Buffers Value="40"/>
      <MaximumFileSize Value="5" FileMode="Circular"/>
      <FileMax Value="3"/>
    </EventCollector>

    <!-- Event Providers -->
    <EventProvider Id="EventProvider_Microsoft-WindowsPhone-TileHelper" Name="B3448AD3-4BE8-4F7C-892B-EA1D69B14ADB" Level="5"/>
    <EventProvider Id="EventProvider_Microsoft-WindowsPhone-AccessoryManagerSvc" Name="68EC658D-C373-4166-996F-D8A757108B27" Level="5"/>

    <!-- Profiles -->
    <Profile Id="TileHelperCategory.Verbose.File" LoggingMode="File" Name="TileManagerCategory" DetailLevel="Verbose" Description="WPDiet TileHelper category profile">
      <Collectors>
        <EventCollectorId Value="EventCollector_TileManager">
          <EventProviders>
            <EventProviderId Value="EventProvider_Microsoft-WindowsPhone-TileHelper"/>
            <EventProviderId Value="EventProvider_Microsoft-WindowsPhone-AccessoryManagerSvc"/>
          </EventProviders>
        </EventCollectorId>
      </Collectors>
    </Profile>
  </Profiles>
</WindowsPerformanceRecorder>
```

**Hinweis**  ETW Anbieter in der vorstehenden XML aufgelistet sind Benutzermodus Komponenten. Wenn Ihr benutzerdefinierte Profil XML-Datei Listen im Kernelmodus Anbieter hinzufügen NonPagedMemory = "true", um die &lt;EventProvider&gt; Element.

 

Weitere Informationen zur Struktur eines benutzerdefinierten Profils XML-Datei finden Sie unter [Authoring Aufzeichnung Profile](http://msdn.microsoft.com/library/windows/hardware/hh448223.aspx).

## <a name="add-your-custom-profile-to-field-medic"></a>Fügen Sie Ihrer benutzerdefinierten Profil Feld Sanitäter hinzu


1.  Erstellen Sie benutzerdefinierte XML-Profildatei, wie oben beschrieben.
2.  Kopieren Sie Ihre benutzerdefinierte XML-Profildatei auf Telefon\\Dokumente\\FieldMedic\\CustomProfiles.
3.  Öffnen Sie die FieldMedic-app, und tippen Sie auf **Erweitert.**
4.  Tippen Sie auf das Feld unter **Wählen Sie, welche ETW-Anbieter verwendet**. Führen Sie einen Bildlauf nach unten zu **Benutzerdefinierten Gruppe**.
5.  Klicken Sie unter **Benutzerdefinierte Gruppe**Sanitäter Feld zeigt die Namen der benutzerdefinierten Profils XML-Dateien, die in Telefon sind\\Dokumente\\FieldMedic\\CustomProfiles. Wählen Sie Ihre benutzerdefinierte Profil. ![Dialogfeld benutzerdefinierte Protokollierung](images/oem-softwaretracing-fieldmedic-customlogging.png)
6.  Erstellen Sie einen Bericht aus, wie beschrieben in [Verwendung Feld Sanitäter einen Bericht](use-field-medic-to-generate-a-report.md). Die daraus resultierenden ETL-Dateien Präfix "Custom"- und befinden sich im Stammverzeichnis des Geräts oder die SD-Karte.

Benutzerdefinierte Profile können ausgewählte zusammen, getrennt von oder mit den regulären Profilen je nach Ihren Anforderungen Protokollierung gemischten sein.

**Hinweis**  
Windows 10 Mobile hat eine Einschränkung eine Variable Anzahl von denen immer durch das standard-Betriebssystem ausgeführt wird Protokollierung 64 insgesamt parallel-Profile. Diese reservierte Betrag hängt von den Typ des Bilds ab. Beispielsweise ist auf Telefonen Retail zurückgestellten Betrags sollte wesentlich niedriger als auf Testgeräten sein. Aus diesem Grund wir wird empfohlen, mehrere ETW-Anbieter zusammen in eine XML-Datei für benutzerdefinierte Profil möglichst bündeln oder auswählen von zu viele ETW-Anbietern parallel vermeiden. Wenn ein Fehler weiterhin auftritt, wenn die Ausführung der Berichte, versuchen Sie es, und deaktivieren Sie einige der Profile.

Weiteren Bedenken ist, dass jedes ausgeführte Profil Betrag des Systemspeichers vor dem Rest des Betriebssystems annimmt. Zu viele parallele protokollierungssitzungen so dass möglicherweise vor allem auf Speichermangel Geräten Leistungseinbußen führen. Diese Speichergröße kann in der XML-Profildatei konfiguriert werden. Die standardmäßigen enthaltenen Profile mit 8 MB pro XML-Datei. Wenn wenig Arbeitsspeicher Probleme untersucht werden, empfehlen wir, ausgeführt nur die Profile, die für dieses bestimmte Untersuchung erforderlich sind.

 

 

 






