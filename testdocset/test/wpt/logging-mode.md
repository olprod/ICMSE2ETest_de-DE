---
title: Protokollierungsmodus
description: Protokollierungsmodus
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 96dc60e4-0550-4cac-b405-9aab923b7435
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: ba4b34f9cecc69118e5c27884cd976db03dcc232
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="logging-mode"></a>Protokollierungsmodus


Wenn Sie ein Profil Windows Performance Aufzeichnung (WPR) definieren, müssen Sie einen Protokollierungsmodus aus den folgenden Optionen auswählen:

-   **Datei**: Zeichnet Protokollierungsdaten in eine sequenzielle Datei

-   **Arbeitsspeicher**: Zeichnet Protokollierungsdaten zirkulären Puffer im Arbeitsspeicher

Die Standardeinstellung für des Protokollierungsmodus ist **Arbeitsspeicher** . *Ein-/ausschalten* Übergänge werden jedoch immer in eine Datei protokolliert.

Datei der Protokollierung wird normalerweise für kurze Aufzeichnungen verwendet für die Sie die Ereignisse erwarten können, die erfasst werden. Arbeitsspeicher der Protokollierung wird normalerweise verwendet, zum Protokollieren von Ereignissen, die zu einem beliebigen Zeitpunkt auftreten können. Wenn WPR Arbeitsspeicher anmeldet, bestimmen Puffergröße und die Detailebene Profil wie lange WPR Daten anmelden kann, bevor alte Ereignisse überschrieben werden.

**Vorsicht**  
Wenn Dateigröße beschränken möchten, wählen Sie **Speicher**. Beim Protokollieren in Datei ist der verfügbare Speicherplatz einzige Begrenzung auf Dateigröße an. Wenn die Datei ist zu groß ist, können Sie nicht analysiert werden in Windows Performance Analyzer (WPA) sein.

 

Beim Erstellen benutzerdefinierter Aufzeichnung Profile, müssen Sie eine Datei und eine Version Speicher in der gleichen Aufzeichnung Profil (.wprp) Definitionsdatei definieren. Wenn Sie ein Profil für eine Aufzeichnung auswählen, müssen Sie entweder die Datei oder im Arbeitsspeicher Version für dieses Ereignis Aufzeichnung verwenden auswählen. Beispiele für benutzerdefinierte Profile finden Sie unter [3. Definitionen Profile](3-profile-definitions.md).

Eine .wprp-Datei kann bis zu vier Profildefinitionen verfügen: eine für jede Kombination aus Detailstufe und Protokollierungsmodus. Die folgenden Einschränkungen erzwungen werden:

-   Der Bezeichner Profil muss im folgenden Format sein: &lt; *Profilname*&gt;. &lt; *DetailLevel*&gt;. &lt; *LoggingMode*&gt;

-   Alle Profile, die in einer einzigen Datei vorhanden sind, benötigen den gleichen Namen.

-   Eine .wprp-Datei muss Profile für Speicher und die Protokollierung Dateimodi enthalten.

Wenn Sie ein benutzerdefiniertes Profil erstellen, müssen Sie die [Puffergröße](buffersize.md) -Element als auch die [Puffer](buffers.md) Element definieren. Sie können die Gesamtmenge des Puffers als eine festgelegte Anzahl von Puffer mit einer Größe, die Sie, in Kilobyte (KB definieren) oder als Prozentsatz des Gesamtspeicherplatzes definieren. Die Anzahl der Standardeinstellung Puffer ist 64, und die Standardgröße beträgt 128 KB.

Die Befehlszeilenschnittstelle WPR können zum Anzeigen der Größe und Anzahl der Puffer, die jedem Provider verwendet.

``` syntax
wpr -profiledetails CPU

Microsoft Windows Performance Recorder Version 6.2.9200


Profile                 : CPU.Verbose.Memory


Collector Name          : NT Kernel Logger
Buffer Size (KB)        : 1024
Number of Buffers       : 613
```

**Hinweis**  
WPR unterstützt nur einwertig *NumberOfBuffers*. Minimale und maximale Puffer unterstützt nicht.

 

Allgemeine Richtlinien zur festzulegenden Puffer lauten folgendermaßen:

-   Ereignis-Stapel erfordern mehr Speicherplatz im Vergleich zu Ereignissen ohne Stapel. Aus diesem Grund WPR verwendet Weitere Puffer und weitere Daten für den gleichen Zeitraum protokolliert.

-   Stellen Sie sicher, dass Ihre Puffer ordnungsgemäß angepasst werden. Wenn Puffer zu groß sind, zu viel Arbeitsspeicher belegt ist und Systemleistung beeinträchtigt wird. Wenn Puffer zu klein sind, Ereignisse können deshalb verloren gehen, und die Ablaufverfolgung wird nicht verwendbar.

-   Beim Protokollieren auf Arbeitsspeicher bestimmt Puffergröße wie lange WPR Daten anmelden kann, bevor alte Ereignisse überschrieben werden. Arbeitsspeicher Spuren wird empfohlen, dass Sie den Puffer als Prozentsatz des Gesamtspeicherplatzes, wie etwa 1 bis 5 % des physischen Arbeitsspeichers, je nach dem Profil festlegen. Es sei denn, das Profil Aufzeichnung ungewöhnlich ausführlich ist, sollte 10 % des physischen Arbeitsspeichers ausreichen.

-   Puffer sind in der Regel kleiner, bei der Anmeldung in eine Datei als beim Anmelden Arbeitsspeicher. Jedoch, wenn die Puffer zu klein sind, werden der Puffer löschen auf dem Datenträger zu häufig. Es sei denn, das Profil Aufzeichnung ungewöhnlich verbose 10 bis 50 MB des physischen Arbeitsspeichers sollte ausreichen.

Weitere Hinweise zum Puffer finden Sie unter [Sitzungen (Windows-Treiber)](http://go.microsoft.com/fwlink/p/?linkid=246706).

## <a name="related-topics"></a>Verwandte Themen


[WPR-Features](wpr-features.md)

[Detailstufe](detail-level.md)

[3. Definitionen für Profil](3-profile-definitions.md)

[Ändern Sie den Protokollierungsmodus](change-the-logging-mode.md)

 

 







