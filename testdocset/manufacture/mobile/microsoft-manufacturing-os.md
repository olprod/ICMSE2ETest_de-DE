---
author: kpacquer
Description: Microsoft Fertigung OS
ms.assetid: 8a46f749-6405-40e8-b3a5-32955e1c0070
MSHAttr: PreferredLib:/library/windows/hardware
title: Microsoft Manufacturing OS
ms.openlocfilehash: 979ac8e44d3e5fc29fb14c4a69b91a4dc6bf359b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="microsoft-manufacturing-os"></a>Microsoft Fertigung OS


Microsoft Fertigung OS (MMOS), eine optimale Konfiguration des Betriebssystems, vereinfacht die effiziente Fertigung. MMOS soll die folgenden Funktionen bereitstellen:

-   Fast Startzeit entsteht ein kleineres Bild, das nur den Code zur Unterstützung von Fertigung erforderlichen enthält Ausführung zu testen. Kleinere Betriebssystemabbild kann schnell, Beschleunigung des Fertigungsprozesses aktualisiert werden.

-   Die Möglichkeit zum Erstellen von Schwelle MMOS OEM-angepasst, die eindeutige Treiber enthält und Testen von Anwendungen.

-   Unterstützung für OEM-entwickelt Komponente auf Dokumentebene testen, zusätzlich zu allen Funktionen Qualität und Kalibrierung testen.

-   Zugriff auf systemeigene Low-Level-APIs für direkte Testen von Hardwarekomponenten Telefon.

-   Die Möglichkeit zum Erstellen eines Mechanismus zum Remote Steuern der testanwendung und Abrufen von Test meldet sich über ein USB-Kommunikationskanal.

-   Keine Abhängigkeit anzuzeigen oder dieses berühren Hardware, um headless-Betrieb zu ermöglichen.

-   Die Möglichkeit, direkt in einer Umgebung Fertigung im MMOS zu starten.

-   Automatisierte Einführung OEM testanwendungen Wenn MMOS gestartet wird.

-   Die Möglichkeit zum Schreiben in die DPP Partition zum Speichern von eindeutigen, pro-Phone-Daten.

-   Batterie geladen wird in UEFI und MMOS unterstützt. Es wird festgelegt, mit einer Funktion festlegen, sodass Partner ein- und ausschalten nach Bedarf aktivieren können. Weitere Informationen finden Sie unter [MMOS Bild Definition](mmos-image-definition.md).

## <a name="span-idworkingwithmmosspanspan-idworkingwithmmosspanspan-idworkingwithmmosspanworking-with-mmos"></a><span id="Working_with_MMOS"></span><span id="working_with_mmos"></span><span id="WORKING_WITH_MMOS"></span>Arbeiten mit MMOS


In diesem Abschnitt wird beschrieben, wie zum Erstellen und flash Schwelle MMOS.

Um mit MMOS arbeiten, führen Sie die folgenden Aufgaben aus:

1.  Erstellen Sie die testanwendung oder andere Tools Fertigung als Pakete. Weitere Informationen finden Sie unter [Creating Pakete](https://msdn.microsoft.com/library/dn756642).

2.  Erstellen Sie ein blinkendes Protokoll und fügen Sie Pakete zur Unterstützung der zur MMOS der Funktionalität hinzu. Weitere Informationen finden Sie unter [Tools blinken](flashing-tools.md).

3.  Erstellen Sie das Bild MMOS. Weitere Informationen finden Sie unter [MMOS image-Definition](mmos-image-definition.md).

4.  Blinken Sie das Bild MMOS des Geräts. Weitere Informationen finden Sie unter [Flash MMOS an das Gerät](flash-mmos-to-the-phone.md).

5.  Bereitstellen von Fertigung Applications. Weitere Informationen finden Sie unter [Bereitstellen und Testen einer Benutzermodus - testanwendung in MMOS](deploy-and-test-a-user-mode-test-application-in-mmos.md).

6.  Ausgewertet, wenn Sie eine WIM MMOS im RAM ausgeführt werden können, um erstellen möchten. Weitere Informationen finden Sie unter [Arbeiten mit WIM MMOS Bilder](working-with-wim-mmos-images.md).

## <a name="span-iddevelopingusermodetestapplicationsspanspan-iddevelopingusermodetestapplicationsspanspan-iddevelopingusermodetestapplicationsspandeveloping-user-mode-test-applications"></a><span id="Developing_user_mode_test_applications"></span><span id="developing_user_mode_test_applications"></span><span id="DEVELOPING_USER_MODE_TEST_APPLICATIONS"></span>Benutzer Anwendungsentwicklung Modus test


So erstellen Sie einen Benutzer Modustest Clientanwendungen zum Testen des Geräts in der Fertigung, führen Sie die folgenden Aufgaben aus:

1.  Entwickeln Sie die Anwendung im Benutzermodus Test unter Verwendung der MMOS-Bibliothek. Weitere Informationen finden Sie unter [testumgebung Fertigung unterstützten APIs](manufacturing-test-environment-supported-apis.md) und [entwickeln MMOS testen Applications](develop-mmos-test-applications.md).

2.  Ein Dienst kann zum Starten einer Anwendung im Benutzermodus Test verwendet werden. Bei Bedarf kann die Anwendung zu testen mit einem Domänencontroller Test auf einem PC Testvorgang steuern und Ergebnisprotokoll kommunizieren.

    Legen Sie zum Konfigurieren des Diensts automatisch gestartet wird, wenn das Betriebssystem startet das **Starten** -Attribut auf "Automatisch" Service-Paket-Konfigurationsdatei ein.  

    ``` syntax
      <Components>
        <Service
          Name="SampleMMOSSvc"
          Start="Auto"
          …
    ```

    Diese Funktion ist nur in MMOS verfügbar.

3.  Einige apps sollte nur dürfen in MMOS ausgeführt werden. Eine API können Sie bestimmen, ob MMOS oder nicht ausgeführt wird. Weitere Informationen finden Sie unter [Determine Wenn MMOS ausgeführt wird](determine-if-mmos-is-running.md).

4.  Rufen Sie zum Auslösen des Geräts in der verbundenen standby Power Zustand wechselt die SetScreenOff-Funktion. Weitere Informationen finden Sie unter [SetScreenOff in den verbundenen Standbymodus zu aufrufen](calling-setscreenoff-to-enter-connected-standby.md).

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Entwickelt testanwendungen MMOS](develop-mmos-test-applications.md)

 

 






