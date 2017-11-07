---
title: Massen-Registrierung
description: "Massen-Registrierung ist eine effiziente Möglichkeit, um eine große Anzahl von Geräten einzurichten, die von einem Server MDM, ohne dass die Geräte ein image verwaltet werden. In Windows 10."
MS-HAID:
- p\_phdevicemgmt.bulk\_enrollment
- p\_phDeviceMgmt.bulk\_enrollment\_using\_Windows\_provisioning\_tool
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: DEB98FF3-CC5C-47A1-9277-9EF939716C87
ms.openlocfilehash: bbdaa348a2bff70463571c1407f6e2122b7270c5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="bulk-enrollment"></a>Massen-Registrierung

Massen-Registrierung ist eine effiziente Möglichkeit, um eine große Anzahl von Geräten einzurichten, die von einem Server MDM, ohne dass die Geräte ein image verwaltet werden. Windows-10 Desktop- und mobilen Geräten können die [Bereitstellung CSP](provisioning-csp.md) für die Registrierung Massen, mit Ausnahme des Azure Active Directory teilzunehmen (Cloud Domäne beitreten) Registrierung Szenarios.

## <a name="typical-use-cases"></a>Typische Anwendungsfälle

-   Einrichten von Geräten in einer Sammeloperation für große Organisationen von MDM verwaltet werden
-   Richten Sie Smart wie Geldautomaten oder Kassenterminals (POS).
-   Schule Computer einrichten.
-   Gewerbliche Maschinen einrichten.
-   Legen Sie handheld POS-Geräte.

Auf dem Desktop können Sie wie ein Active Directory-Konto erstellen "enrollment@contoso.com" , und geben sie nur die Möglichkeit, zu der Domäne beitreten. Nachdem der Desktop mit diesem Konto des Farmadministrators ein Mitglied ist, können dann standard-Benutzer in der Domäne melden Sie sich für die Nutzung. Dies ist besonders bei der Vorbereitung von einer großen Anzahl von Desktops innerhalb einer Domäne verwenden.

Auf die Desktop- und mobilen Geräten können ein Registrierungs-Zertifikat oder Registrierung Benutzername und Kennwort verwenden aus, wie "enroll@contoso.com" und "Enrollmentpassword." Diese Anmeldeinformationen werden in der Bereitstellung Paket verwendet, die Sie verwenden können, um mehrere Geräte mit dem Dienst MDM zu registrieren. Sobald die Geräte verbunden sind, können viele Benutzer diese verwenden.

> **Hinweis**  
> -   Massen-Join wird in Azure Active Directory-Verknüpfung nicht unterstützt.
> -   Massen-Registrierung funktioniert nicht in Intune eigenständigen Umgebung.
> -   Massen-Registrierung funktioniert in System Center Configuration Manager (SCCM) + Intune Hybrid-Umgebung, in der Ppkg von SCCM-Konsole generiert wird.

 

## <a name="what-you-need"></a>Was Sie benötigen

-   Windows-10-Geräte
-   Laden Sie [Windows Assessment and Deployment Kit (ADK)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit), Windows Imaging und Konfiguration Designer (ICD) Tool, um das Tool ICD abzurufen. Weitere Informationen über das Tool ICD finden Sie unter [Windows Imaging und Konfiguration Designer](https://msdn.microsoft.com/library/windows/hardware/dn916113) und [Erste Schritte mit Windows ICD](https://msdn.microsoft.com/library/windows/hardware/dn916112).
-   Registrierung Anmeldeinformationen (Domänenkonto für die Registrierung, generische Registrierung von Anmeldeinformationen für MDM Registrierungs-Zertifikat für MDM)
-   Wi-Fi-Anmeldeinformationen, Computer Namen Schema und keine anderen Einstellungen von Ihrer Organisation benötigt.

    In einigen Organisationen müssen benutzerdefinierte APNs vor der Kommunikation mit der Registrierung Endpunkt oder benutzerdefinierten VPN zum Beitreten zu einer Domäne bereitgestellt werden.

## <a name="create-and-apply-a-provisioning-package-for-on-premise-authentication"></a>Erstellen und Anwenden eines provisioning-Pakets für die Authentifizierung am Standort

Erstellen Sie mit dem ICD ein provisioning Paket mit den Informationen der Registrierung von Ihrer Organisation benötigt. Stellen Sie sicher, dass Sie alle Konfigurationseinstellungen verfügen.

1.  Öffnen Sie das Tool Windows ICD (standardmäßig %windir%\\Program Files (x86)\\Windows Kits\\10\\Assessment and Deployment Kit\\Imaging und Konfiguration Designer\\X86\\ICD.exe).
2.  Klicken Sie auf **Erweiterte Bereitstellung**.

    ![ICD-Startseite](images/bulk-enrollment7.png)
3.  Geben Sie einen Projektnamen ein, und klicken Sie auf **Weiter**.
4.  **Alle Windows-Editionen**, da Provisioning CSP für alle Editionen von Windows 10 üblich ist, klicken Sie auf **Weiter**.
5.  Überspringen Sie **Importieren einer Bereitstellung Paket (optional)** , und klicken Sie auf **Fertig stellen**.
6.  Erweitern Sie **Runtime Einstellungen** &gt; **Arbeitsbereich**.
7.  Klicken Sie auf **diesen**, geben Sie einen Wert in **UPN**, und klicken Sie dann auf **Hinzufügen**.
    Der Benutzerprinzipalname ist ein eindeutiger Bezeichner für die Registrierung. Für die Registrierung Massen muss dies ein Dienstkonto sein, die berechtigt ist, wie mehrere Benutzer registrieren"enrollment@contoso.com".
8.  Klicken Sie im linken Navigationsbereich erweitern Sie den **UPN** , und geben Sie die Informationen für den Rest der Einstellungen für die Registrierung.
    Hier wird die Liste der verfügbaren Einstellungen:
    -   **AuthPolicy** - Select **lokalen**.
    -   **DiscoveryServiceFullUrl** - die vollständige URL für den Suchdienst angeben.
    -   **EnrollmentServiceFullUrl** - Optional und in den meisten Fällen es sollte leer sein.
    -   **PolicyServiceFullUrl** - Optional und in den meisten Fällen es sollte leer sein.
    -   **Clientschlüssel** : Kennwort eine ausführliche Beschreibung dieser Einstellungen finden Sie unter [Bereitstellung CSP](provisioning-csp.md).
    Nachfolgend finden Sie im Screenshot von der ICD an dieser Stelle.
    ![Screenshot von Massen-Registrierung](images/bulk-enrollment.png)
9.  Die anderen Einstellungen wie etwa die Wi-Fi-Verbindungen konfigurieren, sodass das Gerät ein Netzwerk vor der Teilnahme an MDM teilnehmen kann (z. B. **Runtime Einstellungen** &gt; **ConnectivityProfiles** &gt; **WLANSetting**).
10. Wenn Sie fertig sind alle Einstellungen, klicken Sie im Menü **Datei** auf Hinzufügen klicken Sie auf **Speichern**.
11. Klicken Sie im Hauptfenster auf **Exportieren** &gt; **Provisioning-Paket**.

    ![ICD Menü für den export](images/bulk-enrollment2.png)
12. Geben Sie die Werte für das Paket, und geben Sie den Speicherort des Pakets Ausgabe.

    ![Geben Sie ein Paketinformationen](images/bulk-enrollment3.png)
    ![Geben Sie zusätzliche Informationen für Paketinformationen](images/bulk-enrollment4.png)
    ![Dateispeicherort angeben](images/bulk-enrollment6.png)
13. Klicken Sie auf **Erstellen**.

    ![ICB Build-Fenster](images/bulk-enrollment5.png)
14. Das Paket auf einige Testgeräte anwenden, und stellen Sie sicher, dass sie funktionieren. Weitere Informationen finden Sie unter [Anwenden eines Pakets Bereitstellung](#apply-a-provisioning-package).
15. Das Paket auf Ihre Geräte angewendet.

## <a name="create-and-apply-a-provisioning-package-for-certificate-authentication"></a>Erstellen und Anwenden von einer Bereitstellung Paket für die Zertifikatauthentifizierung

Erstellen Sie mit dem ICD ein provisioning Paket mit den Informationen der Registrierung von Ihrer Organisation benötigt. Stellen Sie sicher, dass Sie alle Konfigurationseinstellungen verfügen.

1.  Öffnen Sie das Tool Windows ICD (standardmäßig %windir%\\Program Files (x86)\\Windows Kits\\10\\Assessment and Deployment Kit\\Imaging und Konfiguration Designer\\X86\\ICD.exe).
2.  Klicken Sie auf **Erweiterte Bereitstellung**.
3.  Geben Sie einen Projektnamen ein, und klicken Sie auf **Weiter**.
4.  Wählen Sie **Allgemeine für alle Editionen von Windows**, da Provisioning CSP für alle Editionen von Windows 10 üblich ist.
5.  Überspringen Sie **Importieren einer Bereitstellung (optional) Paket** und klicken Sie auf **Fertig stellen**.
6.  Geben Sie das Zertifikat.
    1.  Wechseln Sie zu **Einstellungen der Common Language Runtime** &gt; **Zertifikate** &gt; **ClientCertificates**.
    2.  Geben Sie eine **CertificateName** , und klicken Sie dann auf **Hinzufügen**.
    3.  Geben Sie den **CertificatePasword**.
    4.  Durchsuchen Sie für **CertificatePath**, und wählen Sie die zu verwendende Zertifikat aus.
    5.  **ExportCertificate** auf False festgelegt.
    6.  Wählen Sie für **KeyLocation** **nur Software**.

    ![Abschnitt ICD-Zertifikate](images/bulk-enrollment8.png)
7.  Geben Sie die Einstellungen Arbeitsbereich.
    1.  **Jahrestag** durfte &gt; **diesen**.
    2.  Geben Sie den **UPN** für die Registrierung, und klicken Sie dann auf **Hinzufügen**.
        Der Benutzerprinzipalname ist ein eindeutiger Bezeichner für die Registrierung. Für die Registrierung Massen muss dies ein Dienstkonto sein, die berechtigt ist, wie mehrere Benutzer registrieren"enrollment@contoso.com".
    3.  Erweitern Sie den **UPN** , und geben Sie dann die Informationen für den Rest der Einstellungen für die Registrierung, auf der linken Spalte.
        Hier wird die Liste der verfügbaren Einstellungen:
        -   **AuthPolicy** - **Zertifikat**auswählen.
        -   **DiscoveryServiceFullUrl** - Geben Sie die vollständige URL für den Suchdienst.
        -   **EnrollmentServiceFullUrl** - Optional und in den meisten Fällen es sollte leer sein.
        -   **PolicyServiceFullUrl** - Optional und in den meisten Fällen es sollte leer sein.
        -   **Clientschlüssel** - Fingerabdruck des Zertifikats.
        Eine ausführliche Beschreibung dieser Einstellungen finden Sie unter [CSP-Bereitstellung](provisioning-csp.md).
8.  Die anderen Einstellungen wie etwa die Wi-Fi-Verbindung konfigurieren, sodass das Gerät ein Netzwerk vor der Teilnahme an MDM teilnehmen kann (z. B. **Runtime Einstellungen** &gt; **ConnectivityProfiles** &gt; **WLANSetting**).
9.  Wenn Sie fertig sind alle Einstellungen, klicken Sie im Menü **Datei** auf Hinzufügen klicken Sie auf **Speichern**.
10. Exportieren Sie und erstellen Sie das Paket (oben beschriebenen Schritte 10 bis 13).
11. Einige Testgeräte das Paket zuzuweisen, und stellen Sie sicher, dass sie funktionieren. Weitere Informationen finden Sie unter [Anwenden eines Pakets Bereitstellung](#apply-a-provisioning-package).
12. Das Paket auf Ihre Geräte angewendet.

## <a name="apply-a-provisioning-package"></a>Anwenden eines provisioning-Pakets

Hier wird die Liste der Themen zum Anwenden einer Bereitstellung Paket:

-   [Anwenden ein Pakets auf dem ersten Ausführen von Setup-Bildschirm (die vordefinierte Experience)](https://technet.microsoft.com/itpro/windows/deploy/provision-pcs-for-initial-deployment#apply-package) - Thema in Technet.
-   [Anwenden eines Pakets zu einem Windows 10 Desktopversion Bild](https://msdn.microsoft.com/library/windows/hardware/dn916107.aspx#to_apply_a_provisioning_package_to_a_desktop_image) - Thema in MSDN
-   [Anwenden eines Pakets zu einem Bild 10 Mobile Windows](https://msdn.microsoft.com/library/windows/hardware/dn916107.aspx#to_apply_a_provisioning_package_to_a_mobile_image) - Thema in MSDN.
-   [Anwenden eines Pakets im Menü Einstellungen](#apply-a-package-from-the-settings-menu) - Thema unten

## <a name="apply-a-package-from-the-settings-menu"></a>Anwenden eines Pakets im Menü Einstellungen

1.  Wechseln Sie zu **Einstellungen** &gt; **Konten** &gt; **Access Arbeit "oder" Schule**.
2.  Klicken Sie auf **Hinzufügen oder Entfernen einer Bereitstellung Packen**.
3.  Klicken Sie auf **Hinzufügen eines Pakets**.

## <a name="a-href-idvalidate-that-the-provisioning-package-was-applied-avalidate-that-the-provisioning-package-was-applied"></a><a href="" id="validate-that-the-provisioning-package-was-applied-"></a>Überprüfen Sie, ob das provisioning Paket angewendet wurde

1.  Wechseln Sie zu **Einstellungen** &gt; **Konten** &gt; **Access Arbeit "oder" Schule**.
2.  Klicken Sie auf **Hinzufügen oder Entfernen einer Bereitstellung Packen**.
    Sie sollten finden Sie unter der Ihr Paket aufgelistet.

## <a name="retry-logic-in-case-of-a-failure"></a>Wiederholen Sie die Logik bei einem Ausfall

Wenn das Bereitstellung Modul einen Fehler vom einen CSP, die sie für die Bereitstellung in einer Zeile 3 Mal wiederholt wird empfängt.

Wenn alle sofortige Versuche fehlschlagen, wird eine verzögerte Aufgabe zum Testen dieses provisioning einem späteren Zeitpunkt erneut gestartet. Er wiederholt 4-fache abklingenden Rate von 15 Minuten -&gt; 1 Stunde -&gt; 4 hr -&gt; "Weiter System starten". Diese Versuche werden von einem Systemkontext ausgeführt werden.

Es wird auch wiederholen, um gelten die Bereitstellung jedes Mal, wenn es gestartet wird, wenn von einer anderen Stelle sowie gestartet.

Darüber hinaus provisioning wird neu gestartet werden in einem Systemkontext nach einer Anmeldung und das System wurde im Leerlauf ([Details im Leerlauf regelbedingungen](https://msdn.microsoft.com/library/windows/desktop/aa383561.aspx)).

## <a name="other-provisioning-topics"></a>Andere Themen mit Bereitstellung

Es folgen Links zu schrittweise Bereitstellung Themen in Technet.

-   [Bestimmung PCs mit apps und Zertifikate für die erste Bereitstellung](https://technet.microsoft.com/itpro/windows/deploy/provision-pcs-with-apps-and-certificates)
-   [Bereitstellung von PCs mit allgemeiner Einstellungen für die erste Bereitstellung](https://technet.microsoft.com/itpro/windows/deploy/provision-pcs-for-initial-deployment)

 






