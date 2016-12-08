---
title: Lokale Videowiedergabe
description: Lokale Videowiedergabe
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: eaf18658-4d3a-472f-a88d-ce13ec04701b
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 1a31ce50dfcd0e64800d9424723a57ce0ddcd6ae
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="local-video-playback"></a>Lokale Videowiedergabe


Als Teil des Auftrags Batterie führen Sie nach unten die Rate des lokalen Videowiedergabe Assessment Verwendung der Batterie des Computers während des ganzen Bildschirms lokale Videowiedergabe.

Zulassen, dass bei der Wiedergabe von lokalen Video Vollbild-Geräte und nicht für der Verwendung der Videowiedergabe jetzt eine minimale Menge Energie übermitteln erforderliche Software für eine noch größere Akkulaufzeit.

Weitere Informationen zu Ergebnisse und Probleme, die mit dieser Bewertung finden Sie unter [Ergebnisse für die lokale Video Wiedergabe Bewertung](results-for-the-local-video-playback-assessment.md).

## <a name="a-href-idbeforeyoubeginabefore-you-begin"></a><a href="" id="beforeyoubegin"></a>Bevor Sie beginnen


Der ersten Ausführung Tipps in Windows 8.1 können Assessment Ergebnisse beeinträchtigen. Um diese zu deaktivieren, führen Sie den folgenden Befehl aus einer Eingabeaufforderung mit erhöhten Rechten, und starten Sie den Computer neu:`reg.exe add "HKLM\Software\Policies\Microsoft\Windows\EdgeUI" /v DisableHelpSticker /t REG_DWORD /d "1" /f`

Bei der Ausführung dieser Bewertung auf Windows 8.1, stellen Sie sicher, dass die Einstellung **Sammeln Analysis Trace** bei der Beurteilung der erwarteten Akkulaufzeit deaktiviert ist. Wenn diese Option aktiviert ist, wird diese Option eine falsche Schätzung erstellt.

Aktivieren Sie Analyse Trace-Auflistung nur, wenn Sie weitere Informationen zum Untersuchen von anderen Probleme im Zusammenhang mit Energie benötigen.

Wenn Sie die lokale Videowiedergabe auf einem PC, die von Windows 8 auf Windows 8.1 aktualisiert wurde ausführen, werden Sie aufgefordert, ein Standardprogramm für die Wiedergabe von MP4-Dateien auswählen. Dies gilt nur für PC, die aktualisiert wurden und PCs mit einer Neuinstallation von Windows 8.1 hat keinen Einfluss auf. Wählen Sie zum Ausführen der Bewertung des Standard-Players bei entsprechender Aufforderung. Oder ändern Sie das Standardprogramm, das MP4-Dateien mithilfe der Systemsteuerung wird geöffnet.

1.  Geben Sie in der **Suche Charm** **Änderung der Dateityp zugeordneten Erweiterung**.

2.  Öffnen der **Systemsteuerung**.

3.  Wählen Sie die Erweiterung MP4 ein, und klicken Sie auf **Programm ändern**.

4.  Wählen Sie das Standard-Programm verwenden, um Dateien MP4 wiedergeben möchten.

### <a name="requirements"></a>Anforderungen

-   Der Computer muss einen Standard-Mediaplayer festgelegt haben, MP4-codierten Inhalt wiedergegeben ist.

-   Der Computer muss ein Video 1080p wiedergegeben werden.

-   DC (Batterie) betrieben muss der Computer ausgeführt werden. Energie Effizienz Aufträge dienen nur auf mobilen Geräten ausgeführt werden. Wenn eine Batterie nicht erkannt wurde, erhalten Sie einen Fehler.

### <a name="recommendations"></a>Empfehlungen

Bevor Sie beginnen, konfigurieren Sie die Einstellungen auf dem Computer, das am häufigsten realistische Szenario möglich, Minderung des generieren Warnungen in den Ergebnissen erstellen. Die folgenden Richtlinien werden Einstellungen empfohlen. Sie sind nicht für die Ausführung des Auftrags erforderlich, aber die Ergebnisse können durch beeinträchtigt, wenn der Computer nicht ordnungsgemäß konfiguriert ist.

-   Stellen Sie sicher, dass auf Ihrem Computer im Flugzeug-Modus ausgeführt wird.

-   Beenden Sie alle nicht absolut ausgeführte Programme.

-   Die Helligkeit des Bildschirms auf mindestens 75 % (200 NT) festgelegt.

-   Installieren Sie und aktivieren Sie Antivirussoftware. Wenn die Antivirensoftware nicht aktiviert ist und ausgeführt wird, können die Ergebnisse realistische Szenarien nicht wider.

    Öffnen Sie in der Systemsteuerung **Action Center**, wählen Sie **Sicherheit**, und überprüfen Sie, dass der **Virenschutz** **aktiviert**ist. Wenn dies nicht der Fall ist, wählen Sie **Aktion Center-Einstellungen ändern** , und wählen Sie dann das Kontrollkästchen **Virenschutz** .

-   Stellen Sie sicher, dass die Richtlinie Power **ausgeglichen**festgelegt ist. Standardmäßig generiert eine beliebige andere Power-Richtlinie eine Warnung ausgegeben, die das Ergebnis beeinflussen können.

    Klicken Sie in der Systemsteuerung öffnen Sie **Energieoptionen**, und wählen Sie dann auf **abgestimmt**.

-   Stellen Sie sicher, dass der Computer konfiguriert ist, damit ein Kennwort nicht erforderlich ist, wenn der Computer aus einem Bildschirmschoner wird.

-   Stellen Sie sicher, dass alle Gerätetreiber ordnungsgemäß installiert sind. Ergebnisse können deutlich abweichen, wenn der Computer mit fehlenden oder falschen Treiber verfügt. Die [Überprüfung der Treiber](driver-verification.md) Bewertung können Sie um Treiberprobleme auf dem Computer zu ermitteln, die Sie bewerten möchten.

-   Die besten Ergebnisse zu erzielen wird empfohlen, dass Sie den Auftrag als gepackte Auftrag ausgeführt. Informationen zum Erstellen und Ausführen eines Auftrags gepackten finden Sie unter [Packen Sie einen Auftrag aus, und führen Sie es auf einem anderen Computer](package-a-job-and-run-it-on-another-computer.md).

### <a name="system-requirements"></a>Systemanforderungen

Sie können dieses Assessment unter den folgenden Betriebssystemen ausführen:

-   Windows 8.1

-   Windows 8.1 RT

-   Windows 10

Unterstützte Architekturen enthalten X86-basierte X64-basierte und ARM-basierte Systeme.

Diese Bewertung können auf einem Windows RT 8.1 System in einem der folgenden Methoden ausgeführt werden:

-   Packen Sie den Bewertungssauftrag zur in der Windows-Assessment-Konsole, und führen sie dann auf Windows RT 8.1. Weitere Informationen zu dieser Option finden Sie unter [Packen Sie einen Auftrag aus, und führen Sie es auf einem anderen Computer](package-a-job-and-run-it-on-another-computer.md).

-   Verwenden von Windows Assessment Services. Weitere Informationen finden Sie unter [Windows Assessment Services](windows-assessment-services-technical-reference.md).

 

 






