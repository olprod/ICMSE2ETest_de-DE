---
title: Liste der WPA-Diagrammen
description: Liste der WPA-Diagrammen
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 71EC5490-7245-45B4-91B0-8B689404A885
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 54d1e0f11208b4412922313047a3683694ef052a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="list-of-wpa-graphs"></a>Liste der WPA-Diagrammen


\[Einige Informationen bezieht sich auf Vorabversionen Produkt, das vor der Freigabe im Handel erheblich geändert werden kann. Microsoft Gewährleistung aus, sei Sie ausdrücklich oder konkludent, im Hinblick auf die hier bereitgestellten Informationen.\]

Das Diagramm Explorer-Fenster in Windows Performance Analyzer (WPA) werden Miniaturansichten alle Diagramme, die Sie zum Anzeigen der Daten der aktuellen Aufzeichnung verwenden können. Die Miniaturansichten sind vom Typ unter den folgenden sechs Kategorien unterteilt:

-   Systemaktivität
-   Berechnung
-   Storage
-   Arbeitsspeicher
-   Video
-   Potenz

Die folgenden Abschnitte beschreiben die verfügbaren Diagramme für jede Art von Grafik.

**Hinweis**  Je nach der Trace erfasst und in der ETL-Datei gespeichert möglicherweise nicht alle Diagramme in den folgenden Tabellen aufgeführten beim Ausführen einer Analyse im Graph-Explorer angezeigt.

 

### <a name="system-activity-graphs"></a>System-Aktivität Diagramme

|                     |                                      |       |
|---------------------|--------------------------------------|-------|
| Diagrammname          | Untertyp Name                         | Hinweise |
| Benutzeroberfläche Verzögerungen           | Geben Sie verzögert nach Prozess,              |       |
| Markiert               | Gruppiert nach Mark                      |       |
| Gerät e/a          | Zeitachse vom Modul                   |       |
|                     | Anzahl nach Modul                     |       |
| Prozesse           | Lebensdauer von Prozess                  |       |
|                     | Vorübergehende Prozessstruktur               |       |
| Aktive Fenster     | Fokus vom Prozess, Thread             |       |
| Bilder              | Vorübergehende Lebensdauer vom Prozess, Bild |       |
|                     | Lebensdauer von Prozess, Bild           |       |
| Generische Ereignisse      | Aktivität, indem Sie Anbieter Aufgabe Opcode   |       |
|                     | Trace Markierungen                        |       |
|                     | VSync DwmFrame                       |       |
| Anwendungszustand   | Anwendungszustand Zeitachse           |       |
| Interessante Bereiche | Interessante Bereiche                  |       |
|                     | Threadaktivitäten                    |       |
| Thread Lebensdauer    | Vom Prozess, Thread                   |       |
|                     | Vom Prozess, Thread Lebensdauer          |       |
| Stapel              | Anzahl von Ereignisname                  |       |

 

### <a name="computation-graphs"></a>Berechnung-Diagrammen

|                        |                                           |       |
|------------------------|-------------------------------------------|-------|
| Diagrammname             | Untertyp                                   | Hinweise |
| CPU-Auslastung (gemessen)    | Nutzung von Prozess Stack             |       |
|                        | DPC und ISR Auslastung durch Modul Stack        |       |
|                        | Nutzung von CPU                        |       |
|                        | Auslastung nach Priorität                   |       |
|                        | Nutzung von Prozessen und Threads         |       |
| CPU-Auslastung (exakt)    | Nutzung von Prozess, Thread            |       |
|                        | Kontext Switch Count vom Prozess, Thread   |       |
|                        | Rate der Kontext Switch nach CPU                |       |
|                        | Zeitachse von CPU                           |       |
|                        | Vom Prozess, Thread Zeitachse               |       |
|                        | Verwendung der nach Priorität unter Kontext Switch beginnen |       |
|                        | Nutzung von CPU                        |       |
| DPC/ISR                | DPC/ISR für die Dauer nach Modul Funktion      |       |
|                        | DPC Dauer von CPU                       |       |
|                        | DPC für die Dauer nach Modul Funktion          |       |
|                        | DPC Zeitachse vom Modul Funktion          |       |
|                        | Für die Dauer nach CPU DPC/ISR                   |       |
|                        | DPC/ISR Zeitachse vom Modul Funktion      |       |
|                        | ISR Dauer                              |       |
|                        | Für die Dauer nach Modul Funktion ISR          |       |
|                        | ISR Zeitachse vom Modul Funktion          |       |
| CPU-Auslastung (attributierten) | Nutzung von Thread-Prozessaktivität  |       |

 

### <a name="storage-graphs"></a>Speicher-Diagrammen

|                    |                                                  |       |
|--------------------|--------------------------------------------------|-------|
| Diagrammname         | Untertyp                                          | Hinweise |
| Mini Filter Verzögerungen | Zeitachse von Treiber, Prozess, Thread              |       |
|                    | Anzahl von Mini Filter                             |       |
| Datenträgerverwendung         | Nutzung von Datenträger, Priorität                    |       |
|                    | Aktivität nach Typ e/a-Prozess                     |       |
|                    | Anzahl von e/a-Typ, Priorität                      |       |
|                    | Anzahl von Prozess, e/a-Typ                       |       |
|                    | Datenträger-Offset                                      |       |
|                    | E/a-Zeit vom Prozess, e/a-Typ                      |       |
|                    | Reaktionszeit Prozess Pfadname, der Stack        |       |
|                    | Größe der Prozess, Pfadname, der Stack                |       |
|                    | Durchsatz von Prozess, e/a-Typ                   |       |
|                    | Nutzung von Datenträger                              |       |
|                    | Auslastung nach Priorität e/a-Typ                 |       |
|                    | Vom Prozess Pfadname, Stack Auslastung         |       |
| Registrierung           | Landkreis von Vorgang, Prozess, Schlüssel                |       |
|                    | Kumulative Handleanzahl vom Prozess, Schlüssel          |       |
|                    | Verstrichene Zeit durch den Vorgang, Prozess oder Schlüssel          |       |
|                    | Verstrichene Zeit nach Prozess, Operation, Schlüssel          |       |
| E/a           | Anzahl nach Typ                                    |       |
|                    | Aktivität pro Prozess, Thread-Typ                |       |
|                    | Anzahl nach Prozess, Thread-Typ                   |       |
|                    | Die Dauer nach Thread-Prozesstyp                |       |
|                    | Größe von Dateinamen, Prozess, Stapel für Lese-/Schreibzugriff |       |
|                    | Größe von Prozess, Stapel für Lese-/Schreibzugriff            |       |

 

### <a name="memory-graphs"></a>Arbeitsspeicher-Diagrammen

|                               |                                |       |
|-------------------------------|--------------------------------|-------|
| Diagrammname                    | Untertyp                        | Hinweise |
| RAM-Auslastung            | Auslastung nach Kategorie        |       |
| Seitenfehler                   | Anzahl von Prozess               |       |
| Schwerer Fehler                   | Anzahl                          |       |
|                               | Vom Prozess zählen, Dateiname    |       |
|                               | E/a-Zeit vom Prozess, Dateiname  |       |
| VirtualAlloc Commit Lebensdauer | Ausstehende Commit vom Prozess  |       |
| Verarbeitet                       | Ausstehende Count vom Prozess   |       |
|                               | Zeigt die Gesamtanzahl von Prozess    |       |
| Momentaufnahmen virtueller Arbeitsspeicher      | Standard                        |       |
| Pool-Diagrammen                   | Ausstehende Größe von ausgelagert, Tag |       |

 

### <a name="video-graphs"></a>Video-Diagrammen

|                      |                               |       |
|----------------------|-------------------------------|-------|
| Diagrammname           | Untertyp                       | Hinweise |
| DX Frames            | Dauer von Prozess FlipType |       |
| GPU Auslastung (FM) | Vom Prozess GPU                |       |
| DWM Frame-Details    | DWM Framerate                |       |
|                      | DWM Frame E2E                 |       |
|                      | DWM Frame GPU                 |       |
|                      | Rechteck nach Typ             |       |

 

### <a name="power-graphs"></a>Power-Diagrammen

Text

|                                        |                                        |       |
|----------------------------------------|----------------------------------------|-------|
| Diagrammname                             | Untertyp                                | Hinweise |
| Häufigkeit der CPU                          | Häufigkeit von CPU                       |       |
| CPU im Leerlauf Staaten                        | Status nach Typ Cpu                     |       |
|                                        | State Diagramm durch Flags                 |       |
|                                        | State Diagramm nach Typ, Cpu             |       |
| Gerät Dstate                          | DState nach Typ Gerät                 |       |
| Komponente PoFx FState                  | FState vom Gerät, Komponente            |       |
| PoFx Gerät Power-Anforderung          | Power gefordertes vom Gerät                    |       |
| PDC Resiliency Aktivität                | Resiliency Aktivität nach Aktivierung       |       |
| Plattform-Leerlauf                    | Plattform IdleState                     |       |
|                                        | Plattform IdleState, indem Zeit            |       |
|                                        | Plattform IdleState, gezielte und aktuelle Kosten |       |
| ThermalZone Temperatur                | Temperature(K) von ThermalZone          |       |
| Schnelle entladen                          | Schnelle entladen                          |       |
| System Latenztoleranz               | System Wartezeit Tolerance(ns)           |       |
| SPM Szenarien                          | SPM für die Dauer nach Status Szenario        |       |
|                                        | SPM Dauer nach Szenario Zustand        |       |
| Prozessor-Profile                     | Prozessor-Profile                     |       |
| Prozessor-Dienstprogramm                      | Dienstprogramm-Prozessor                   |       |
|                                        | Affinitized-Dienstprogramm von Prozessor       |       |
| CPU-Auslastung                  | Nutzung von Prozessor               |       |
| Prozessor Parkplatz Zustand                | Parkplatz Zustand von Prozessor             |       |
| Core Parkplatz unmittelbare Gleichzeitigkeit | Instant Parallelität von Knoten Parken    |       |
| Core Parkplatz Parallelität               | Parallelität von Knoten Parken            |       |
| Core Parkplatz Cap Zustand                 | Zurückholen Sie Cap Kerne durch das Parken von Knoten       |       |
| Prozessor-Leistung                  | Leistung durch Prozessor               |       |
| Prozessor-Häufigkeit                    | Häufigkeit von Prozessor                 |       |
| Prozessor-Integritätsregeln                  | Einschränkungen von Prozessor               |       |

 

## <a name="related-topics"></a>Verwandte Themen


[Registerkarte Analyse](analysis-tab.md)

[Diagramm-Explorer](graph-explorer.md)

[WPA-Benutzeroberfläche](wpa-user-interface.md)

 

 







