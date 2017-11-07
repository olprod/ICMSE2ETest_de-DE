---
title: "Verwenden Sie zum Erstellen eines Berichts Feld Sanitäter"
description: "Verwenden Sie zum Erstellen eines Berichts Feld Sanitäter"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3afb13d4-30e5-4eb0-ab13-315bfa74723a
ms.openlocfilehash: 6b013a994f8ecd3417ad45a83826c305932f0da0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="use-field-medic-to-generate-a-report"></a>Verwenden Sie zum Erstellen eines Berichts Feld Sanitäter


In diesem Thema wird erläutert, wie zum Erstellen eines Berichts (mit der Bezeichnung "Aufzeichnung" einen Bericht). Informationen zum Feld Sanitäter finden Sie unter [Sanitäter dar](field-medic.md).

## <a name="recording-a-field-medic-report"></a>Aufzeichnen eines Berichts Feld Sanitäter


Gehen Sie folgendermaßen vor, um Geräteinformationen in einem Feld Sanitäter-Bericht aufzuzeichnen.

1.  Führen Sie das Feld Sanitäter app.

2.  Tippen Sie auf **Erweitert**. Wählen Sie die Kategorien, die im Bericht enthalten sein sollen.

    ![Erweiterte Optionen im Dialogfeld Feld Sanitäter](images/oem-field-medic-wp-ss-20140109-0003.png)

3.  Drücken Sie die Schaltfläche **zurück** zum Hauptbildschirm Feld Sanitäter zurückgegeben.

4.  Tippen Sie auf **Protokollierung starten**.

    ![Feld Sanitäter Menü](images/oem-field-medic-wp-ss-20140109-0001.png)

5.  Nachdem Sie die Protokollierung starten, zeigt Feld Sanitäter die Capture verstrichene Zeit unter der Option **Protokollierung stoppen** an. Schließen Sie Feld Sanitäter durch Drücken der Taste **zurück** oder **Starten** . Reproduzieren Sie das Problem, dem Sie Informationen zu erfassen möchten.

    **Hinweis**  
    ETW-Protokollierung für die ausgewählten Kategorien bleibt auch nach der Gerät neu gestartet wird, aktiviert, bis Sie die Protokollierung beenden.

     

    ![Feld Medics Menü Bericht in der Sitzung](images/oem-field-medic-wp-ss-20140109-0005.png)

6.  Nachdem Sie das Problem reproduziert haben, führen Sie Feld Sanitäter, und tippen Sie auf **Protokollierung stoppen**.

    **Hinweis**  
    Es kann fünf Sekunden dauern oder länger für Sanitäter beenden ETW-Sitzungen und erstellen Sie die Berichtsdateien dar.

     

    ![Feld Medics Menü beenden reporting](images/oem-field-medic-wp-ss-20140109-0008.png)

7.  Anzeigen können, bearbeiten und löschen die Liste der aufgezeichneten Berichte durch Tippen auf dem Hauptbildschirm **Berichte anzeigen** .

    ![Feld Medics Berichte im Menü](images/oem-field-medic-wp-ss-20140109-0011.png)

8.  Berichte im Bildschirm Berichte dargestellt heißen standardmäßig mit dem Format des "WPB\_\#\#\#\_Datum\_Zeit."

    Sie können drücken und halten einen Bericht in der Liste zu **Löschen**, **Bearbeiten**oder **Anzeigen** des Berichts zugeordneten Dateien.

9.  ![Feld Medics Berichtsoptionen](images/oem-field-medic-wp-ss-20140109-0010.png)

Tools wie Xperf und Tracerpt und ETWDump können Sie um die ETL-Dateien zu überprüfen.

## <a name="a-href-idview-log-files-in-a-field-medic-report-aview-log-files-in-a-field-medic-report"></a><a href="" id="view-log-files-in-a-field-medic-report-"></a>Anzeigen der Protokolldateien in einem Feld Sanitäter-Bericht


1.  Um einen Bericht Feld Sanitäter extrahieren möchten, schließen Sie das Gerät an einem Computer mit einem USB-Kabel. Kopieren Sie den Bericht Feld Sanitäter vom Gerät (im Stammverzeichnis des Geräts oder im Stammverzeichnis der SD-Karte), mit dem PC. Jeden Ordner in diesem Verzeichnis stellt einen anderen Bericht und mehrere ETW-Protokolldateien enthält.
2.  Suchen Sie auf Ihrem Computer ETWDump im Windows-Treiberkits.

    Beispiel: C:\\Programmdateien (x86)\\Windows Kits\\10\\ToolFunnel\\EtwDump\\2.0\\EtwDump.exe

3.  Suchen Sie die Manifestdateien ETW im Windows-Treiberkits.

    Beispiel: C:\\Programmdateien (x86)\\Windows Kits\\10\\Manifeste

    Die Dateien Mainifest (MC) enthalten Informationen über die Formatierung, die ETWDump wird verwendet, um die Protokolldateien (ETL) decodieren an.

4.  Öffnen Sie ein Eingabeaufforderungsfenster, und stellen Sie sicher, dass Ihre Path-Umgebungsvariablen der Pfad zur ETWDump.exe ist.

    Es folgt ein Beispiel der Verwendung von EtwDump zum Decodieren der FieldMedic-Kontakte-Calendar.etl-Protokolldatei.

    ``` syntax
    etwdump FieldMedic-Contacts-Calendar.etl -import "C:\Program Files (x86)\Windows Kits\10\Manifests" -o FmCC.csv –of CSV
    ```

ETWDump ist eine der mehrere Tools, die Sie zum Decodieren ETW-Protokolldateien verwenden können. Es folgen einige andere Tools, die Sie zum Decodieren ETW-Protokolldateien verwenden können:

[Xperf](https://msdn.microsoft.com/library/windows/hardware/hh162920.aspx)

XPerf ist in der Windows-Anpassung und Bereitstellung Kit (ADK) enthalten.

[Tracerpt](https://technet.microsoft.com/library/cc732700.aspx)

Tracerpt ist in Windows enthalten.

## <a name="specify-advanced-options"></a>Legen Sie erweiterte Optionen


Öffnen Sie die app Sanitäter dar, und tippen Sie auf **Erweitert**. Wie bereits gezeigt, können Sie die ETW-Anbieter Kategorien auswählen, die Sie in den Bericht einschließen möchten. Sie können auch angeben, ob diese Elemente in den Bericht einschließen:

-   Systemprotokolle und Absturz sichert (Standard oder vollständig)
-   Netlogs
-   QXDM Protokolle

**Hinweis**  Wenn Absturz speichert erhalten möchten, müssen Sie für Feedback im OS Einstellungen Hauptbildschirm bestätigt. Nachdem Sie bestätigt, ist in regelmäßigen Abständen Absturz Dumpinformationen an Microsoft gesendet, wenn das Gerät geladen wird und mit einem Wi-Fi-Netzwerk verbunden. Ein Feld Sanitäter Bericht in der Sitzung ist, die Berichte Absturz werden nicht an Microsoft gesendet, aber in das Feld Sanitäter Berichte enthalten sind. Alle Absturz speichert, die nicht aktuell an Microsoft hochgeladen werden, bevor ein Feld Sanitäter Bericht eingetragen ist auch in den nächsten Feld Sanitäter Bericht enthalten sind und werden nicht hochgeladen werden an Microsoft anschließend.

 

![Feld Medics Menü "Erweitert"](images/oem-field-medic-wp-ss-20140114-0002.png)

Sie können auch angeben, dass Berichte auf einer SD-Karte gespeichert werden, wenn diese auf dem Gerät verfügbar ist. Dies ist hilfreich für Geräte, die viel Speicherplatz zum Speichern von Berichten nicht aufweisen.

Tippen Sie auf **auswählen, wo Berichte gespeichert**, und wählen Sie dann auf **SDCard**

![im Feld "Kategorien" Sanitäter](images/oem-field-medic-wp-ss-20140109-0003.png)

## <a name="a-href-idspecify-custom-loggers-aspecify-custom-loggers"></a><a href="" id="specify-custom-loggers-"></a>Geben Sie benutzerdefinierte Protokollierungsmodule


Feld Sanitäter kann Berichte aus benutzerdefinierten Protokollierungsmodule enthalten, die Sie angeben. Weitere Informationen finden Sie unter [benutzerdefinierte Protokollierung mit Feld Sanitäter](custom-logging-with-field-medic.md).

## <a name="related-topics"></a>Verwandte Themen


[Feld Sanitäter](field-medic.md)

 

 







