---
author: kpacquer
Description: "Erfassung-Client für Windows Phone"
ms.assetid: 2d62208f-8ba3-4034-a853-a16434c2b26d
MSHAttr: PreferredLib:/library/windows/hardware
title: "Erfassung-Client für Windows Phone"
ms.openlocfilehash: ee121dbd60eda7cbdda5a658f321f3ec8ee63a68
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="ingestion-client-for-windows-phone"></a>Erfassung-Client für Windows Phone


Der Aufnahme-Client ist ein Satz von [Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkId=389794) -Cmdlets, die Kommunikation mit Diensten zum Abrufen und senden Signieren von Code und Aktualisieren von Anfragen zu und von Microsoft verwendet werden.

-   [Initialize-FirmwareSubmission-cmdlet](initialize-firmwaresubmission-cmdlet.md)

-   [Neue FirmwareSubmission-cmdlet](new-firmwaresubmission-cmdlet.md)

-   [Get-SignedFirmwareSubmission-cmdlet](get-signedfirmwaresubmission-cmdlet.md)

-   [Neue RequestForUpdate-cmdlet](new-requestforupdate-cmdlet.md)

-   [Neue RequestForMicrosoftUpdate-cmdlet](new-requestformicrosoftupdate-cmdlet.md)

-   [Get-RequestForUpdate-cmdlet](get-requestforupdate-cmdlet.md)

-   [Anforderung-UpdateCancellation-cmdlet](request-updatecancellation.md)

Um die Aufnahme-Client zu verwenden, müssen die folgenden Aufgaben, die genauer erläutert werden weitere in diesem Thema abgeschlossen werden.

1.  Folgen Sie den Anweisungen im Abschnitt [Melden Sie sich für den Einzelhandel Paket signieren und Updates](#provision-certs) weiter unten in diesem Thema, um die OEM x. 509-Zertifikate zu senden und jedes Zertifikat zugeordneten öffentlichen und privaten Schlüssel verwalten.

2.  Befolgen Sie die Anweisungen im Abschnitt [Installieren der erforderlichen Software](#install-pre) weiter unten in diesem Thema So installieren Sie die vorausgesetzte Software, um die Aufnahme-Client verwenden.

3.  Befolgen Sie die Anweisungen im Abschnitt [Installieren Sie den Client Aufnahme](#install) weiter unten in diesem Thema, um die Aufnahme-Client installieren und Konfigurieren der Erfassung-Clients zum Verwenden des bereitgestellten Zertifikats aus dem vorherigen Schritt.

## <a name="span-idprovisioncertsspanspan-idprovisioncertsspansign-up-for-retail-package-signing-and-update-submissions"></a><span id="provision_certs"></span><span id="PROVISION_CERTS"></span>Melden Sie sich für den Einzelhandel Paket signieren und Update Übermittlungen


In diesem Abschnitt werden die Schritte, die Sie ausführen müssen, um für den Einzelhandel Paket signieren und Updates zu registrieren. Wenn dieser Prozess abgeschlossen ist, können Sie Pakete und Updates an Microsoft für die Signierung Verkaufsversion übermitteln. Allgemeine Informationen zu Retail und Test Signieren von Code finden Sie unter [Signieren von Code](https://msdn.microsoft.com/library/windows/hardware/dn756634).

Um sicherzustellen, dass die Kommunikation zwischen OEMs und Microsoft sicher ist, verwendet der Aufnahme Client x. 509-Zertifikate für die Authentifizierung. Im Rahmen der Anmeldung ist OEM erforderlich, um einen gültigen öffentlichen Schlüssel mit x. 509-Zertifikat an Microsoft senden, bevor die Aufnahme-Client verwendet werden kann. Dies ermöglicht Microsoft zum Identifizieren des Benutzers des Clients und entsprechenden Zugriff auf ihre Daten zu autorisieren. Der private Schlüssel ist vom OEM beibehalten und Zugriff auf die Updateserver verwendet.

Um für das Paket und Update anmelden anmelden, Übermitteln einer Anforderung per E-mail an <WPSignOB@Microsoft.com> mit dem Betrefftitel "Onboarding-Anforderung für \[Ihr OEM-Firmenname\]". Diese E-mail muss die folgenden Anhänge beinhalten:

1.  OEM Onboarding Formulars, das [hier](http://go.microsoft.com/fwlink/p/?LinkId=394161)heruntergeladen werden kann. Schrittweise Anleitung finden Sie unter [Exemplarische Vorgehensweise für Onboarding Signieren von Code und Updates](http://cmsresources.windowsphone.com/devcenter/oem/downloads/Onboarding-for-Code-Signing-and-Updates.pptx).

2.  Eine oder mehrere code signierenden Authentifizierungszertifikate. Für jedes Zertifikat zählen:

    1.  Der öffentliche Teil des Schlüssels angefügte als ein. CER-Datei.

    2.  Das Zertifikat, der Anfrageformular Bereitstellung. Das Formular enthält Details zu den Anforderungen an Zertifikate und Informationen zum Ausfüllen des Formulars. Sie können das Zertifikat provisioning Anfrageformular [hier](http://go.microsoft.com/fwlink/p/?LinkId=394159)herunterladen.

Es dauert in der Regel eine Geschäftszeiten diese Anforderungen. Nachdem Sie die Onboarded haben, erhalten Sie eine e-Mail-Nachricht, die Anweisungen zum Herunterladen der signierenden Tools und Dokumentation enthalten wird wie updateanforderungen und Weitere Informationen zu übermitteln.

**X. 509-Zertifikat-Richtlinien**

-   OEM besitzt das Zertifikat und ist verantwortlich für die Sicherheit. Der private Schlüssel des Zertifikats stellt die Identität des OEM. OEM muss bewährte branchenüblichen Methoden verwalten und als Anlage wichtige und vertraulich zu schützen. OEM möglicherweise mehrere Zertifikate bieten, aber sie werden aufgefordert, die Anzahl der Zertifikate gering zu halten. Dadurch wird sichergestellt, dass der OEM nicht durch eine Richtlinie häufige zeitbasierte OCSP für Zertifikate belastet werden wird und Betriebsaufwand reduziert werden sinken. In der Regel wird erwartet, dass ein OEM geografischen Standort ein oder zwei Zertifikate verfügen.

-   In der Standardeinstellung ist dasselbe Zertifikat für Produktions- und Präproduktion Umgebungen bereitgestellt, sofern nicht anders ausdrücklich vom OEM angefordert.

-   OEM teilt mit, dass Microsoft bei der ein Zertifikat gesperrt ist, läuft ab oder für alle anderen deshalb, Microsoft, um das Zertifikat deaktivieren erforderlich ist.

## <a name="span-idinstallprespanspan-idinstallprespaninstall-the-prerequisite-software"></a><span id="install_pre"></span><span id="INSTALL_PRE"></span>Installieren der erforderlichen software


Der Aufnahme Client erfordert Windows Identity Foundation und Windows PowerShell 3.0.

Die empfohlenen Schritte zum Bereitstellen eines Computers für den Client sind wie folgt:

1.  Installieren Sie Windows Server 2012 R2, Windows 8.1 oder einem anderen Betriebssystem unterstützt.

2.  Wenden Sie alle Patches, die mithilfe von Windows Update an.

3.  Falls erforderlich, fügen Sie den Computer mit einer active Directory-Domäne.

4.  Nachdem Sie der Computer mit der Domäne angehört, überprüfen Sie Windows Update und wenden Sie alle Patches an.

5.  Führen Sie für Windows Server-Editionen zwei zusätzlichen Schritte aus:

    1.  Konfigurieren Sie verstärkte Sicherheitskonfiguration für Internet Explorer durch Klicken auf **IE konfigurieren**.

        ![IEESC-1](images/oem-internet-explorer-enhanced-security-configuration-1.png)

    2.  Klicken Sie im Dialogfeld verstärkte Sicherheitskonfiguration für Internet Explorer, wählen Sie **deaktiviert** für Administratoren und für Benutzer **deaktiviert** festgelegt.

        ![IEESC-2](images/oem-internet-explorer-enhanced-security-configuration-2.png)

6.  Installieren Sie Windows Identity Foundation (WIF). Windows 8 ist WIF als OS Feature verfügbar. Es kann mithilfe von "Windows-Funktionen ein- oder ausschalten" in der Systemsteuerung Programme und Features installiert werden. Für Windows Server 2008 R2 herunter, und installieren Sie WIF von <http://go.microsoft.com/fwlink/p/?LinkId=389793>.

7.  Installieren Sie Windows PowerShell 3.0 (Windows Management Framework 3.0). Windows 8 ist PowerShell als OS Feature verfügbar. Es kann mithilfe von **Windows-Features aktivieren oder deaktivieren** in der Systemsteuerung Programme und Features installiert werden. Für Windows Server 2008 R2 herunter, und installieren Sie Windows PowerShell aus [http://go.microsoft.com/fwlink/p/?linkid=240290](http://go.microsoft.com/fwlink/p/?LinkID=240290)aus.

8.  Verwenden Sie Windows Update, um alle Patches anzuwenden.

9.  Wenn die erforderlichen Komponenten installiert sind, sind die nächsten Schritte Bereitstellen ein x. 509-Zertifikat, und installieren Sie den Aufnahme-Client mithilfe der Anweisungen in diesem Dokument.

## <a name="span-idinstallspanspan-idinstallspaninstall-the-ingestion-client"></a><span id="install"></span><span id="INSTALL"></span>Installieren Sie den Client aufnehmen


**Hinweis**  
Die 64-Bit-Version des Clients Aufnahme wird ab 12/9/2013 nicht mehr unterstützt. Wenn die 64-Bit-Version installiert ist, muss diese deinstalliert werden und muss die 32-Bit-Version installiert sein.

 

Der Aufnahme-Client kann unter den folgenden Betriebssystemen installiert werden:

-   Windows Server 2012 R2

-   Windows 8.1

-   WindowsServer 2012

-   Windows 8

-   Windows Server 2008 R2

-   Windows 7

**Msiexec** aus einer Eingabeaufforderung mit erhöhten Rechten ausführen, muss der Aufnahme-Client installiert sein. Informationen zu den bestimmten Werten, die verwendet werden wird weiter unten in diesem Dokument behandelt.

Diese Werte können später durch Bearbeiten dieser XML-Konfigurationsdatei, die während der Installation %ProgramFiles(x86)% erstellt wird geändert\\Microsoft\\WP Aufnahme Client\\Module\\ Microsoft.Phone.PartnerServices.Client\\Microsoft.Phone.PartnerServices.Client.dll.config.

Standardmäßig wird die Installation eine Benutzeroberfläche bereit. Um zu verhindern, dass die Benutzeroberfläche angezeigt wird, verwenden Sie die/qn, stillen Option. Weitere Informationen zu **Msiexec**finden Sie unter [Msiexec](http://go.microsoft.com/fwlink/p/?LinkId=389794).

**Die Syntax der Installation**

Der Befehl aus, um die Installation des Clients muss die folgenden Parameter:

-   *BASEURI*: der URI des Diensts Microsoft-Partner.

-   *NAMESPACE*: Steuerelement für den Microsoft-Partner-Dienst zugreifen.

-   *MYCLIENTCERTIFICATEPATH*: der vollqualifizierte Pfad zu einer Zertifikatsdatei, die den privaten Schlüssel enthält.

-   *PFXPASSWORD*: das Kennwort des der Zertifikatsdatei an, die in der MYCLIENTCERTIFICATEPATH-Parameter angegeben ist.

Der Parameter angegeben wurden im folgenden Format:

``` syntax
msiexec /I WPIngestionClient.msi 
    BASEURI="[Microsoft service environment URL]"
    NAMESPACE="[Microsoft access control identifier]" 
    MYCLIENTCERTIFICATEPATH="[Path of OEM PFX file]"
    PFXPASSWORD="[Password of PFX file]"
    /l*v install.log
```

Führen Sie nach Erhalt ein gültiges x. 509-Zertifikat aus den folgenden installieren:

-   Produktion (Retail Bild signing): Installieren Sie den Client um Abrufen von Anforderungen in der produktionsumgebung von Microsoft zu senden:

    ``` syntax
    msiexec /I WPIngestionClient.msi 
        BASEURI="http://wp8partnerservicesv1.cloudapp.net:7159"
        NAMESPACE="wp8partnerservicesv1" 
        MYCLIENTCERTIFICATEPATH="C:\Certificates\OemSecretCertificateWithPrivateKey.pfx"
        PFXPASSWORD="Password-Of-OemSecretCertificateWithPrivateKey.pfx"
        /l*v install.log
    ```

In diesem Beispiel "C:\\Zertifikate\\OemSecretCertificateWithPrivateKey.pfx" wird als Platzhalter verwendet, um den Speicherort des ein gültiges x. 509-Zertifikat vom OEM erstellte darstellen.

**Hinweis**  
-   Den privaten Schlüssel Zertifikatsdatei und das Kennwort, die als Parameter zum Installieren von verwendet werden, so konfigurieren Sie das x. 509-Zertifikat im Zertifikatspeicher des lokalen Computers angegeben. Das Kennwort nicht an anderer Stelle gespeichert sind und nicht mit Microsoft ausgetauscht werden.

 

Nach dem Installieren des Clients aufnehmen, erstellt der Installationsbefehl der Ordner %ProgramData%\\Microsoft\\WP Aufnahme Client\\. Dieser Ordner enthält die Unterordner Sicherung und Protokolle. Unterordner "Backup" wird verwendet, um die Clientkonfiguration für die Deinstallation zu speichern. Der Logs Unterordner wird verwendet, um die Client-Cmdlet diagnostic Protokollinformationen gespeichert.

## <a name="span-idtroubleshootingspanspan-idtroubleshootingspantroubleshooting-the-ingestion-client"></a><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Problembehandlung für die Aufnahme-client


**Ausnahmen**

`Microsoft.Phone.PartnerServices.Exceptions.UnknownErrorException.`Ein Fehler ist aufgetreten. Die HTTP-Anforderung wurde mit Clientauthentifizierungsschema "Anonymous" verboten...

Wenn die Ausnahme "Microsoft.Phone.PartnerServices.Exceptions.UnknownErrorException" ausgelöst wird, wenn die Cmdlets verwendet werden, ist das Problem durch die HTTP-Proxyeinstellungen innerhalb des Netzwerks der OEM wahrscheinlich verursacht. Die maximal zulässige Nachrichtengröße in den HTTP-Proxy konfiguriert ist zu klein, um die gesendeten Pakete hochladen, oder der Port, mit dem Hochladen der Pakete, wird blockiert. Korrigieren die HTTP-Proxyeinstellungen innerhalb des Netzwerks der OEM und versuchen Sie es erneut.

**Option verbose**

Die Cmdlets unterstützen zusätzliche Informationen über die PowerShell gemeinsame **Verbose** -Parameter Verarbeitung Befehl.

Standardmäßig die verbose Nachrichten werden nicht angezeigt, aber dies kann durch Angeben des allgemeinen Parameters auf einen beliebigen Befehl geändert werden. Bei Aktivierung schreibt das Cmdlet Text in den verbose Stream in Windows PowerShell.

Berücksichtigen Sie z. B., in dem eine vorhandene signierten Firmware Versendung abgerufen wird. Dies ist die knappe Ausgabe einer solchen Cmdlets:

``` syntax
PS> Get-SignedFirmwareSubmission –TicketId TKT-SIGN-TEST-BTUADL -DownloadDirectory C:\temp | Format-List

TicketId : TKT-SIGN-TEST-BTUADL
File     : c:\temp\OemTest.TKT-SIGN-TEST-BTUADL.zip
```

Wenn Sie der **Verbose** -Parameter angegeben wird, wird zusätzliche Informationen für die Interaktion mit dem Dienst angezeigt:

``` syntax
PS> Get-SignedFirmwareSubmission –Verbose –TicketId TKT-SIGN-TEST-BTUADL -DownloadDirectory C:\temp | Format-List

VERBOSE: Parameter assignment: 'TicketId' = TKT-SIGN-TEST-BTUADL.
VERBOSE: Downloading OemTest.TKT-SIGN-TEST-BTUADL.zip in 4194304 byte chunks.
 File is 17341441 bytes long.
VERBOSE: Start reading chunk 0, 0 - 4194303 bytes.
VERBOSE: Start reading chunk 1, 4194304 - 8388607 bytes.
VERBOSE: Start reading chunk 2, 8388608 - 12582911 bytes.
VERBOSE: Start reading chunk 3, 12582912 - 16777215 bytes.
VERBOSE: Start reading chunk 4, 16777216 - 17341440 bytes.
VERBOSE: Writing block number 0 of size 4194304.
VERBOSE: Writing block number 1 of size 4194304.
VERBOSE: Writing block number 2 of size 4194304.
VERBOSE: Writing block number 3 of size 4194304.
VERBOSE: Writing block number 4 of size 564225.
VERBOSE: File successfully downloaded to OemTest.TKT-SIGN-TEST-BTUADL.

TicketId : TKT-SIGN-TEST-BTUADL
File     : c:\temp\OemTest.TKT-SIGN-TEST-BTUADL.zip
```

**Von Diagnoseprotokollen**

Ist der Standardspeicherort der diagnostic Ausgabe vom Client aufnehmen: "C:\\Ordner" ProgramData "\\Microsoft\\WP Aufnahme Client\\Protokolle"

**Ausweiten ein Problem an Microsoft**

Um ein Problem an Microsoft ausweiten, senden Sie die folgende Informationen durch das Senden eines Fehlers mithilfe der Fehler, dem Ihnen Zugriff auf bereitgestellt wurde.

-   Beschreibung des versuchte Szenarios

-   Screenshots

-   Protokolldateien

-   Konfigurationsdatei: Microsoft.Phone.PartnerServices.Client\\Microsoft.Phone.PartnerServices.Client.dll.config

-   Ticket-ID

-   Korrelationswert. Dies kann über das [Cmdlet Get-SignedFirmwareSubmission](get-signedfirmwaresubmission-cmdlet.md)abgerufen werden.

 

 