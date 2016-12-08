---
title: "Automatisieren Sie Neustarts, bevor Sie eine Bewertung ausführen"
description: "Automatisieren von Neustarts vor dem Ausführen einer Bewertung"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4aadbc09-9c0a-4b38-b79d-989906c0aa50
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: e17d93d41b4eac22c3b8396a41de77bccca39183
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="automate-reboots-before-you-run-an-assessment"></a>Automatisieren Sie Neustarts, bevor Sie eine Bewertung ausführen


Einige Bewertung müssen den Computer neu starten, während die Bewertung ausgeführt wird. Wenn Sie beabsichtigen, einen Computer manuell zu überwachen, während die Bewertung ausgeführt wird, können Sie sich jedes Mal anmelden, die einem des Computers Neustart. Aber wenn Sie nicht zum Überwachen des Computers, während die Bewertung ausgeführt wird, können Sie den Computer automatisch anmelden konfigurieren. Die Verfahren in diesem Thema werden die Ereignisse:

-   So konfigurieren Sie einen Computer ohne Anmeldung aufgefordert, indem Sie in der Registrierung anpassen. Dieses Verfahren wird empfohlen, wenn Sie die Windows-Konsole zur Bewertung Bewerten von einem lokalen Computer verwenden.

-   Informationen zum Erstellen eines Benutzerkontos, das automatisch an einem Computer nach einem Neustart angemeldet wird. Es wird empfohlen, dieses Verfahren für Testcomputern, die nicht auf die Domäne oder andere potenzielle Sicherheitslücken im Netzwerk aufweisen.

**Anpassen der Einstellungen für die automatische Anmeldung in der Registrierung**

1.  Klicken Sie auf **Start**, geben Sie **regedit ein**, und klicken Sie dann auf **Registrierungs-Editor**.

2.  Suchen Sie im Registrierungs-Editor folgenden Registrierungsschlüssel:

    **HKEY\_LOKALE\_MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\Winlogon**

3.  Doppelklicken Sie auf den Eintrag **DefaultUserName** , geben Sie Ihren Benutzernamen ein, und klicken Sie dann auf **OK**.

4.  Doppelklicken Sie auf den Eintrag **DefaultPassword** , geben Sie Ihr Kennwort ein, und klicken Sie dann auf **OK**.

    **Sicherheitshinweis:**

    Das Kennwort wird in Klartext gespeichert und stellt ein Sicherheitsrisiko darstellen. Es wird empfohlen, dass Sie Testkonto verwenden und den Wert des Schlüssels entfernen, wenn Sie die ausgeführte Bewertung abgeschlossen sind.

5.  Wenn der Wert **DefaultPassword** nicht vorhanden ist, gehen Sie folgendermaßen vor:

    1.  Klicken Sie auf **Bearbeiten**, klicken Sie auf **neu**, und klicken Sie dann auf **Zeichenfolgenwert**.

    2.  Geben Sie in das Feld **Wert** **DefaultPassword**.

    3.  Vergewissern Sie sich, die in das Feld **Datentyp** **REG\_SU** ausgewählt ist.

    4.  Geben Sie Ihr Kennwort ein, in das Feld **Wert** .

    5.  Klicken Sie auf **OK** , um die Änderungen zu speichern.

    6.  Ändern Sie den Wert des Schlüssels **Automatische Anmeldung** von 0 (FALSE) auf 1 (TRUE). Auf diese Weise können die Funktion für automatische Anmeldung.

    7.  Exit-Registrierungs-Editor.

6.  Starten Sie den Computer neu, und stellen Sie sicher, dass er Sie automatisch angemeldet.

    **Hinweis**  
    Die automatische Anmeldung zu umgehen und als anderer Benutzer anmelden möchten, halten Sie die UMSCHALTTASTE gedrückt, nachdem Sie sich abmelden oder Windows neu gestartet wird.

     

Sie nach Abschluss der Bewertung auf dem Computer ausgeführt können Sie die registrierungseinstellungen auf die ursprünglichen Werte des Anmeldevorgangs regulären folgen ändern.

**Vorbereiten eines Benutzerkontos und Deaktivieren der sicheren Anmeldung**

1.  Erstellen Sie einen einzelnen Standard-Benutzer für den Computer an.

    **Wichtige**  
    -   Gewähren Sie nicht dem Benutzer ein Kennwort.

    -   Nicht zulassen oder eine Verbindung mit einer Domäne konfigurieren.

     

2.  Löschen Sie alle anderen Benutzer, Kennwörter und Domäne-Verbindungen.

3.  Deaktivieren der sicheren Anmeldung folgende Schritte:

    1.  Klicken Sie auf **Start**, und geben Sie dann **Netplwiz** zum Suchen und öffnen Sie das Dialogfeld **Benutzerkonten** .

    2.  Klicken Sie auf der Registerkarte **Erweitert** das Kontrollkästchen Sie **müssen Benutzer STRG + Alt + Entf** .

Dieses Konto für die einzelnen Benutzer kann die Bewertung auf dem Computer ohne alle Überwachung oder manuelle Anmeldung Schritte ausführen.

## <a name="related-topics"></a>Verwandte Themen


[Ein-/ausschalten Übergang Leistung](onoff-transition-performance.md)

[Speicherbedarf](memory-footprint.md)

[Windows-Assessment-Konsole](windows-assessment-console.md)

 

 







