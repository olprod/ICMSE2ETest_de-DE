---
title: SharedPC CSP
description: SharedPC CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 31273166-1A1E-4F96-B176-CB42ECB80957
ms.openlocfilehash: 99f1099efadf9b163a6e4deebc7dbf04add8813a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sharedpc-csp"></a>SharedPC CSP


Dienstanbieter SharedPC Konfiguration wird verwendet, um die Einstellungen für PC gemeinsame Nutzung zu konfigurieren.

Das folgende Diagramm zeigt die Konfiguration SharedPC dienstanbieterobjekten Management im Strukturformat von Open Allianz Verwaltung mobiler Geräte (OMA DM), OMA-Clientbereitstellung und Enterprise-DM verwendet.

![sharedpc](images/sharedpc-csp.png)

<a href="" id="--vendor-msft-sharedpc"></a>**./Vendor/MSFT/SharedPC**  
Den Stammknoten für den Dienstanbieter für SharedPC-Konfiguration.

Der unterstützte Vorgang ist abrufen.

<a href="" id="enablesharedpcmode"></a>**EnableSharedPCMode**  
Ein boolescher Wert, der angibt, ob gemeinsame PC-Modus aktiviert ist.

Die unterstützten Vorgänge sind Get und ersetzen.

Durch Festlegen dieser Wert auf True wird die Aktion, die ein Gerät auf den PC Shared-Modus konfigurieren.

Der Standardwert ist False.

<a href="" id="setedupolicies"></a>**SetEduPolicies**  
Optional Ein boolescher Wert, der angibt, dass die Richtlinien für eine Umgebung mit Education definiert festgelegt werden soll, wenn SharedPC Modus zu konfigurieren.

>  **Hinweis**  Wenn verwendet, muss dieser Wert festgelegt werden, bevor die Aktion auf den Knoten **EnableSharedPCMode** ausgeführt wird.

 

Die unterstützten Vorgänge sind Get und ersetzen.

Der Standardwert lautet True.

<a href="" id="setpowerpolicies"></a>**SetPowerPolicies**  
Optional Ein boolescher Wert, der angibt, dass die Power-Richtlinien festgelegt werden soll, wenn SharedPC Modus zu konfigurieren.

>  **Hinweis**  Falls verwendet, muss dieser Wert vor der Aktion für den Knoten **EnableSharedPCMode** festgelegt werden.

 

Die unterstützten Vorgänge sind Get und ersetzen.

Der Standardwert lautet True.

<a href="" id="maintenancestarttime"></a>**MaintenanceStartTime**  
Optional Ein Ganzzahlwert, der die tägliche Anfangszeit der Wartung Stunde angibt. Angesichts in Minuten aus Mitternacht. Der Bereich ist 0 und 1440.

>  **Hinweis**  Wenn verwendet, muss dieser Wert festgelegt werden, bevor die Aktion auf den Knoten **EnableSharedPCMode** ausgeführt wird.

 

Die unterstützten Vorgänge sind Get und ersetzen.

Der Standardwert ist 0 (00: 00 Uhr).

<a href="" id="signinonresume"></a>**SignInOnResume**  
Optional Ein boolescher Wert, der Anmeldung erfordert, bei Festlegung auf true festgelegt ist, im, wenn das Gerät reaktiviert aus dem Standbymodus.

>  **Hinweis**  Wenn verwendet, muss dieser Wert festgelegt werden, bevor die Aktion auf den Knoten **EnableSharedPCMode** ausgeführt wird.

 

Die unterstützten Vorgänge sind Get und ersetzen.

Der Standardwert lautet True.

<a href="" id="sleeptimeout"></a>**SleepTimeout**  
Optional Eine ganze Zahl, die die Zeit in Sekunden an, die im Anmeldebildschirm ein Gerät befindet, bevor der Benutzer abmelden. Dieser Wert auf 0 festgelegt wird verhindert, dass das Standbymodus Timeout auftritt.

>  **Hinweis**  Wenn verwendet, muss dieser Wert festgelegt werden, bevor die Aktion auf den Knoten **EnableSharedPCMode** ausgeführt wird.

 

Die unterstützten Vorgänge sind Get und ersetzen.

Der Standardwert ist 3600 (1 Stunde).

<a href="" id="enableaccountmanager"></a>**EnableAccountManager**  
Ein boolescher Wert, der den Konto-Manager für freigegebene PC-Modus ermöglicht.

>  **Hinweis**  Wenn verwendet, muss dieser Wert festgelegt werden, bevor die Aktion auf den Knoten **EnableSharedPCMode** ausgeführt wird.

 

Die unterstützten Vorgänge sind Get und ersetzen.

Der Standardwert lautet True.

<a href="" id="accountmodel"></a>**AccountModel**  
Konfiguriert, welche Art von Konten dürfen den PC zu verwenden.

>  **Hinweis**  Wenn verwendet, muss dieser Wert festgelegt werden, bevor die Aktion auf den Knoten **EnableSharedPCMode** ausgeführt wird.

 

Die unterstützten Vorgänge sind Get und ersetzen.

In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) - dürfen nur Gastkonten.
-   1 – nur sind in die Domäne eingebundener Konten aktiviert.
-   2 - Domänenverbund und Gast Konten dürfen.

<a href="" id="deletionpolicy"></a>**DeletionPolicy**  
Konfiguriert, wenn Benutzerkonten gelöscht wurden.

>  **Hinweis**  Wenn verwendet, muss dieser Wert festgelegt werden, bevor die Aktion auf den Knoten **EnableSharedPCMode** ausgeführt wird.

 

Die unterstützten Vorgänge sind Get und ersetzen.

In der folgenden Liste sind die unterstützten Werte:

-   0 – löschen sofort.
-   1 (Standard) – unter Disk Space Schwellenwert löschen.

<a href="" id="diskleveldeletion"></a>**DiskLevelDeletion**  
Wird den prozentuale Anteil des Speicherplatzes auf einem PC verbleiben zwischengespeicherte Konten gelöscht werden, um Speicherplatz freizugeben. Konten, die der am längsten inaktiv waren werden zuerst gelöscht werden.

>  **Hinweis**  Wenn verwendet, muss dieser Wert festgelegt werden, bevor die Aktion auf den Knoten **EnableSharedPCMode** ausgeführt wird.

 

Der Standardwert ist 25.

Wenn beispielsweise die Anzahl der **DiskLevelCaching** auf 50 festgelegt ist und die Anzahl der **DiskLevelDeletion** auf 25 (beide Standardwerte) festgelegt ist. Konten werden während der freie Speicherplatz mehr als 25 % wird zwischengespeichert. Wenn der freie Speicherplatz weniger als 25 % (die Anzahl der Löschvorgang) während eines Wartungszeitraums ist, werden Konten (ältesten letzten verwendeten zuerst) gelöscht, bis der freie Speicherplatz über 50 % (Anzahl Zwischenspeichern) ist. Konten werden sofort unter Registrieren von einem Konto gelöscht, wenn freier Speicherplatz befindet sich unter den Schwellenwert für die Löschung und Festplattenspeicher zur Verfügung sehr niedrig, unabhängig davon steht, ob der PC-Option aktiv verwendet oder nicht.

Die unterstützten Vorgänge sind Get und ersetzen.

<a href="" id="disklevelcaching"></a>**DiskLevelCaching**  
Legt den Prozentsatz des verfügbaren Speicherplatzes die ein PC verfügen muss, bevor es beendet zwischengespeicherte Konten löschen.

>  **Hinweis**  Wenn verwendet, muss dieser Wert festgelegt werden, bevor die Aktion auf den Knoten **EnableSharedPCMode** ausgeführt wird.

 

Der Standardwert ist 50.

Wenn beispielsweise die Anzahl der **DiskLevelCaching** auf 50 festgelegt ist und die Anzahl der **DiskLevelDeletion** auf 25 (beide Standardwerte) festgelegt ist. Konten werden zwischengespeichert werden sollen, während der freie Speicherplatz mehr als 25 % ist. Konten werden können, wenn der freie Speicherplatz weniger als 25 % (die Anzahl der Löschvorgang) während eines Wartungszeitraums ist, gelöscht (ältesten zuletzt verwendeten zuerst), bis sich der freie Speicherplatz über 50 % (die Nummer Zwischenspeichern) befindet. Konten werden unmittelbar unter Registrieren von einem Konto gelöscht werden, wenn freier Speicherplatz unter den Schwellenwert für die Löschung ist und Speicherplatz sehr niedrig, unabhängig davon, ob der PC aktiv verwendet oder nicht.

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






