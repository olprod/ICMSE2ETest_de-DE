---
title: CertificateStore CSP
description: CertificateStore CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0fe28629-3cc3-42a0-91b3-3624c8462fd3
ms.openlocfilehash: dc828e3cf3b0b995021902029175001c94c912d4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="certificatestore-csp"></a>CertificateStore CSP


Dienstanbieter CertificateStore Konfiguration wird verwendet, um secure Sockets Layer (SSL), intermediate hinzufügen, und selbstsignierte Zertifikate.

> **Hinweis**   Konfigurationsdienstanbieter CertificateStore unterstützt keine Installation Clientzertifikaten.

 

Für den CSP CertificateStore kann nicht ersetzen Verwendung des Befehls, wenn der Knoten bereits vorhanden ist.

Das folgende Diagramm veranschaulicht das CertificateStore Configuration Service Provider Management-Objekts im Strukturformat von Open Allianz Verwaltung mobiler Geräte (OMA DM) sowohl OMA-Clientbereitstellung verwendet.

![Bereitstellung\-Csp\-Certificatestore](images/provisioning-csp-certificatestore.png)

<a href="" id="root-system"></a>**Stamm-System**  
Definiert den Zertifikatspeicher, der enthält Stamm- oder selbstsignierte Zertifikate.

Unterstützte Vorgang ist Get.

> **Hinweis**  Stamm-System wird Groß-/Kleinschreibung beachtet. Verwenden Sie für die Installation von Stammzertifikaten vorwärts RootCATrustedCertificates CSP.

 

<a href="" id="ca-system"></a>**CA-System**  
Definiert den Zertifikat-Speichers, der kryptografischen Informationen, einschließlich zwischengeschaltete Zertifizierungsstellen enthält.

Unterstützte Vorgang ist Get.

> **Hinweis**  CA-System wird Groß-/Kleinschreibung beachtet. Verwenden Sie die RootCATrustedCertificates CSP vorwärts zum Installieren von Zertifikaten.

 

<a href="" id="my-user"></a>**Meine / Benutzer**  
Definiert den Zertifikatspeicher, der öffentliche Schlüssel für Clientzertifikate enthält. Dies wird nur von Enterprise-Servern verwendet, um den öffentlichen Schlüssel, der ein Clientzertifikat zu übertragen. Das Clientzertifikat wird vom Client Gerät verwendet, um sich an den Enterprise-Server für die Verwaltung von Geräten und Herunterladen von unternehmensanwendungen zu authentifizieren.

Unterstützte Vorgang ist Get.

> **Hinweis**  Meine / Benutzer wird Groß-/Kleinschreibung beachtet.

 

<a href="" id="my-system"></a>**Meine / System**  
Definiert den Zertifikatspeicher, der öffentlichen Schlüssel für Clientzertifikat enthält. Dies wird nur von Enterprise-Server zum Schieben nach unten den öffentlichen Schlüssel für die Client-Zertifikat. Das Client-Zertifikat wird vom Gerät verwendet, sich selbst mit dem Enterprise-Server für Gerätemanagement und Herunterladen von Enterprise-app authentifizieren.

Unterstützte Vorgang ist Get.

> **Hinweis**  Meine / System wird Groß-/Kleinschreibung beachtet.

 

<a href="" id="certhash"></a>***CertHash***  
Definiert den SHA1-Hash für das Zertifikat. Der 20-Byte-Wert des SHA1-Zertifikathash wird als ein hexadezimaler Zeichenfolgenwert angegeben.

Unterstützte Vorgänge sind Get, löschen, und Ersetzen Sie.

<a href="" id="certhash-encodedcertificate"></a>***CertHash*/EncodedCertificate**  
Erforderlich. Gibt das x. 509-Zertifikat als Base64-codierte Zeichenfolge. Der Base64-String-Wert kann keine zusätzliche Formatierung Zeichen wie etwa eingebetteten Zeilenvorschübe usw. enthalten.

Unterstützte Vorgänge sind Get, hinzufügen, löschen, und ersetzen.

<a href="" id="certhash-issuedby"></a>***CertHash*/IssuedBy**  
Erforderlich. Gibt den Namen der Aussteller des Zertifikats zurück. Dies ist gleichbedeutend mit dem *Aussteller* -Element in der CERT\_INFO-Datenstruktur.

Unterstützte Vorgang ist Get.

<a href="" id="certhash-issuedto"></a>***CertHash*/IssuedTo**  
Erforderlich. Gibt den Namen des Betreffs Zertifikats zurück. Dies ist gleichbedeutend mit dem *Betreff* -Element in der CERT\_Datenstruktur INFO.

Unterstützte Vorgang ist Get.

<a href="" id="certhash-validfrom"></a>***CertHash*/ValidFrom**  
Erforderlich. Gibt das Startdatum des die Gültigkeit des Zertifikats zurück. Dies ist gleichbedeutend mit dem *nicht vor* -Element in der CERT\_INFO-Struktur.

Unterstützte Vorgang ist Get.

<a href="" id="certhash-validto"></a>***CertHash*/ValidTo**  
Erforderlich. Gibt das Ablaufdatum des Zertifikats zurück. Dies ist gleichbedeutend mit dem *nicht nach* Element in der CERT\_INFO-Struktur.

Unterstützte Vorgang ist Get.

<a href="" id="certhash-templatename"></a>***CertHash*/TemplateName**  
Erforderlich. Gibt den Namen der Vorlage an.

Unterstützte Vorgang ist Get.

<a href="" id="my-scep"></a>**Meine/SCEP**  
Erforderlich für die Registrierung von Zertifikaten einfache Registrierung SCEP (Certificate Protocol). Der übergeordnete Knoten des Zertifikats SCEP gruppieren bezogene Einstellungen.

Unterstützte Vorgang ist Get.

> **Hinweis**  Verwenden Sie die ClientCertificateInstall CSP vorwärts SCEP Zertifikate installiert. Alle Erweiterungen der SCEP in dieser CSP geschieht.

 

<a href="" id="my-scep-uniqueid"></a>**Meine/SCEP / ***_UniqueID_**  
Für die Registrierung von Zertifikaten SCEP erforderlich. Eine eindeutige ID zu zertifikatanforderungen für die Registrierung zu unterscheiden. Format ist Knoten.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="my-scep-uniqueid-install"></a>* **Meine/SCEP/UniqueID*/Install**  
Für die Registrierung von Zertifikaten SCEP erforderlich. Übergeordneten Knoten, der Gruppe SCEP Zertifikat installieren verwandte Anforderung. Format ist Knoten.

Unterstützte Vorgänge sind Sie ersetzen, hinzufügen und löschen.

> **Hinweis**   Obwohl die untergeordneten Knoten unter Install ersetzen Befehle unterstützen, nachdem der Befehl Exec an das Gerät gesendet wird, dauert das Gerät die Werte, die festgelegt werden, wenn der Befehl Exec akzeptiert wird. Erwarten Sie jedoch nicht die Änderung des Werts Knoten, die auftritt, nachdem Sie der Befehl Exec zugestimmt haben, auf das aktuelle Gegenstand Registrierung auswirken. Überprüfen Sie den Wert der Status-Knoten, und stellen Sie sicher, dass das Gerät nicht zu einem unbekannten Zeitpunkt vor dem Ändern der Werte der untergeordneten Knoten ist.

 

<a href="" id="my-scep-uniqueid-install-serverurl"></a>* ***Meine/SCEP/UniqueID/Install/ServerURL **  
Für die Registrierung von Zertifikaten SCEP erforderlich. Gibt den Registrierung Zertifikatserver. Der Server kann mehrere Server angeben URLs durch ein Semikolon getrennt. Werttyp ist Zeichenfolge.

Unterstützte Vorgänge sind Get, hinzufügen, löschen, und ersetzen.

<a href="" id="my-scep-uniqueid-install-challenge"></a>* ***Meine/SCEP/UniqueID/Install/Herausforderung **  
Für die Registrierung von Zertifikaten SCEP erforderlich. B64 codiert SCEP Registrierung Herausforderung. Werttyp ist chr.

Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

Herausforderung wird kurz nach der Befehl Exec angenommen wurde gelöscht.

<a href="" id="my-scep-uniqueid-install-ekumapping"></a>**Meine/SCEP /* UniqueID*/Install/EKUMapping** erforderlich sind. Gibt die erweiterte Schlüsselverwendung und Betreff zu SCEP Serverkonfiguration. Die Liste der OIDs werden durch ein Pluszeichen (+) getrennt **+ **, beispielsweise OID1 + OID2 + OID3. Werttyp ist chr.

Unterstützte Vorgänge sind Get, hinzufügen, löschen, und ersetzen.

<a href="" id="my-scep-uniqueid-install-keyusage"></a>* ***Meine/SCEP/UniqueID/Install/Schlüsselverwendung **  
Erforderlich für die Registrierung. Gibt die Enhanced Key Usage Bits (0 x 80, 0 x 20, 0xA0, usw.) für das Zertifikat im Dezimalformat. Der Wert sollte mindestens zweite (0 x 20) oder vierten (0 x 80) oder beide Bits festgelegt. Konfiguration schlägt fehl, wenn der Wert keinen diese Bits festgelegt. Werttyp ist eine ganze Zahl.

Unterstützte Vorgänge sind Get, hinzufügen, löschen, und ersetzen.

<a href="" id="my-scep-uniqueid-install-subjectname"></a>* ***Meine/SCEP/UniqueID/Install/SubjectName **  
Erforderlich. Gibt den Antragstellernamen an. Werttyp ist chr.

Unterstützte Vorgänge sind Get, hinzufügen, löschen, und ersetzen.

<a href="" id="my-scep-uniqueid-install-keyprotection"></a>* ***Meine/SCEP/UniqueID/Install/KeyProtection **  
Optional Gibt den Speicherort des privaten Schlüssels. Obwohl der private Schlüssel durch TPM geschützt ist, ist es nicht mit TPM-PIN geschützt. SCEP registrierten Zertifikat unterstützt keine PIN TPM-Schutz.

Unterstützte Werte sind die folgenden:

-   1 – privater Schlüssel ist von TPM-Gerät geschützt.

-   2 – privater Schlüssel ist von TPM-Gerät geschützt, wenn das Gerät TPM unterstützt.

-   3 (Standard) – privater Schlüssel ist nur in der Software KSP gespeichert.

Werttyp ist eine ganze Zahl.

Unterstützte Vorgänge sind Get, hinzufügen, löschen, und ersetzen.

<a href="" id="my-scep-uniqueid-install-retrydelay"></a>* ***Meine/SCEP/UniqueID/Install/RetryDelay **  
Optional Gibt die Wartezeit für Gerät "Wiederholen" in Minuten, wenn der Server SCEP ausstehend sendet, an. Standardwert ist 5, und der Mindestwert ist 1. Werttyp ist eine ganze Zahl.

Unterstützte Vorgänge sind Get, die Sie hinzufügen und löschen.

<a href="" id="my-scep-uniqueid-install-retrycount"></a>* ***Meine/SCEP/UniqueID/Install/RetryCount **  
Optional Spezielle zu SCEP. Gibt die Gerät Retry Zeiten, wenn der Server SCEP ausstehende Status sendet. Werttyp ist eine ganze Zahl. Standardwert ist 3. Max-Wert darf nicht größer als 30 sein. Wenn es größer als 30 ist, wird das Gerät 30 verwenden. Der Minimalwert ist 0, was bedeutet, keine "Wiederholen dass".

Unterstützte Vorgänge sind Get, hinzufügen, löschen, und ersetzen.

<a href="" id="my-scep-uniqueid-install-templatename"></a>* ***Meine/SCEP/UniqueID/Install/TemplateName **  
Optional Der Objektbezeichner des Zertifikats Vorlagenname. Beachten Sie, dass dieser Name in der Regel vom Server SCEP ignoriert wird. aus diesem Grund muss MDM Server in der Regel nicht bereit. Werttyp ist chr.

Unterstützte Vorgänge sind Get, die Sie hinzufügen und löschen.

<a href="" id="my-scep-uniqueid-install-keylength"></a>* ***Meine/SCEP/UniqueID/Install/erkannt wurden **  
Erforderlich für die Registrierung. Geben Sie die Länge des privaten Schlüssels (RSA). Werttyp ist eine ganze Zahl. Gültige Werte sind 1024, 2048, 4096. NGC Schlüssellängen unterstützt sollte angegeben werden.

Unterstützte Vorgänge sind Get, hinzufügen, löschen, und ersetzen.

<a href="" id="my-scep-uniqueid-install-hashalgorithm"></a>* ***Meine/SCEP/UniqueID/Install/HashAlgorithm **  
Erforderlich für die Registrierung. Hash-Algorithmus Familie (SHA-1, SHA-2, SHA-3) durch den MDM Server angegeben. Wenn mehrere Hash-Algorithmus-Familien angegeben werden, müssen sie mit getrennt +.

Werttyp ist chr.

Unterstützte Vorgänge sind Get, hinzufügen, löschen, und ersetzen.

<a href="" id="my-scep-uniqueid-install-cathumbprint"></a>* ***Meine/SCEP/UniqueID/Install/CAThumbprint **  
Erforderlich. Gibt den Fingerabdruck Stammzertifizierungsstelle. Es ist ein 20-Byte-Wert des SHA1 Zertifikathash als ein hexadezimaler Zeichenfolgenwert angegeben. Bei Client der SCEP Server authentifiziert, überprüft Zertifizierungsstellen-Zertifikat vom Server SCEP für eine Übereinstimmung mit diesem Zertifikat. Die Authentifizierung schlägt fehl, wenn es nicht übereinstimmt. Werttyp ist chr.

Unterstützte Vorgänge sind Get, hinzufügen, löschen, und ersetzen.

<a href="" id="my-scep-uniqueid-install-subjectalternativenames"></a>**Meine/SCEP /* UniqueID*/Install/SubjectAlternativeNames* * Optional. Gibt den alternativen Antragstellernamen an. Mehrere alternative Namen können angegeben werden. Jeder Name ist die Kombination aus Namensformat + tatsächlichen Namen. Finden Sie in der Definition des Typs Name in MSDN. Jedes Paar wird durch Semikolon getrennt. Beispielsweise werden mehrere alternative Antragstellernamen im Format bearbeitet * &lt;nameformat1&gt;*+*&lt;tatsächlichen name1&gt;*; * &lt;Namensformat 2&gt; * +*&lt;actual name2&gt;*. Werttyp ist chr.

Unterstützte Vorgänge sind Get, hinzufügen, löschen, und ersetzen.

<a href="" id="my-scep-uniqueid-install-validperiod"></a>* ***Meine/SCEP/UniqueID/Install/ValidPeriod **  
Optional Gibt die Einheiten für den Gültigkeitszeitraum. Werttyp ist chr.

Unterstützte Vorgänge sind Get, hinzufügen, löschen, und ersetzen.

Gültige Werte sind die folgenden:

-   Tage (Standard)
-   Monate
-   Jahre

> **Hinweis**   Das Gerät sendet MDM Server erwartet Gültigkeitsdauer des Zertifikats (ValidPeriodUnits + ValidPeriod) des Servers SCEP nur im Rahmen der Registrierung zertifikatanforderung. Wie dieser gültigen Zeitraum verwendet wird, um das Zertifikat zu erstellen, hängt von den MDM Server.

 

<a href="" id="my-scep-uniqueid-install-validperiodunits"></a>* ***Meine/SCEP/UniqueID/Install/ValidPeriodUnits **  
Optional Gibt die gewünschte Anzahl von Einheiten, die in Gültigkeitszeitraum und kann SCEP Serverkonfiguration verwendet. Standardwert ist 0. Die Einheiten sind in ValidPeriod Knoten definiert. Der Gültigkeitszeitraum durch MDM angegeben überschreibt den Gültigkeitszeitraum in der Zertifikatvorlage angegeben. Beispielsweise bedeutet Wenn ValidPeriod Tage ist und ValidPeriodUnits 30 ist, dies, dass die gültige Gesamtdauer 30 Tage ist. Werttyp ist eine ganze Zahl.

Unterstützte Vorgänge sind Get, hinzufügen, löschen, und ersetzen.

> **Hinweis**   Das Gerät sendet MDM Server erwartet Gültigkeitsdauer des Zertifikats (ValidPeriodUnits + ValidPeriod) des Servers SCEP nur im Rahmen der Registrierung zertifikatanforderung. Wie dieser gültigen Zeitraum zum Erstellen des Zertifikats verwendet wird, hängt von den MDM Server ab.

 

<a href="" id="my-scep-uniqueid-install-enroll"></a>* ***Meine/SCEP/UniqueID/Installieren/registrieren **  
Erforderlich. Löst das Gerät, um die Registrierung von Zertifikaten zu starten. Der MDM Server kann später das Gerät, um zu ermitteln, ob das neue Zertifikat hinzugefügt wird Abfragen. Werttyp ist null, was bedeutet, dass dieser Knoten nicht über einen Wert enthält.

Unterstützte Vorgang ist Exec.

<a href="" id="my-wstep-certthumbprint"></a>**Meine/WSTEP/CertThumbprint**  
Optional Gibt den aktuellen MDM Client Zertifikatfingerabdruck zurück. Wenn Erneuerung erfolgreich ist, zeigt es den Fingerabdruck des neuen Zertifikats. Wenn Erneuerung fehlschlägt oder wird gerade durchgeführt, zeigt es den Fingerabdruck des das Zertifikat, das erneuert werden müssen. Werttyp ist chr.

Unterstützte Vorgang ist Get.

<a href="" id="my-scep-uniqueid-status"></a>* **Meine/SCEP/UniqueID*/Status**  
Erforderlich. Gibt den aktuellen Status für das Zertifikat aufgrund der Registrierung Anforderung. Werttyp ist chr.

Unterstützte Vorgang ist Get.

Gültige Werte sind die folgenden:

-   1 – erfolgreich fertig gestellt wurde.

-   2 – ausstehende. Das Gerät hat die Aktion nicht abgeschlossen, aber den Server SCEP ausstehende Antwort erhalten hat.

-   16 - Aktion ist fehlgeschlagen.

-   32 – unbekannt.

<a href="" id="my-scep-uniqueid-errorcode"></a>* **Meine/SCEP/UniqueID*/ErrorCode**  
Optional Der Ganzzahlwert, der das HRESULT des letzten Registrierung Fehlercodes angibt.

Unterstützte Vorgang ist Get.

<a href="" id="my-scep-uniqueid-certthumbprint"></a>* **Meine/SCEP/UniqueID*/CertThumbprint**  
Optional Gibt den Fingerabdruck des aktuellen Zertifikats an, ob Registrierung von Zertifikaten erfolgreich ausgeführt wird. Es ist ein 20-Byte-Wert des SHA1 Zertifikathash als ein hexadezimaler Zeichenfolgenwert angegeben. Werttyp ist chr.

Unterstützte Vorgang ist Get.

<a href="" id="my-scep-uniqueid-respondentserverurl"></a>* **Meine/SCEP/UniqueID*/RespondentServerUrl**  
Erforderlich. Gibt die URL des Servers, die auf die Registrierung Anforderung reagiert SCEP zurück. Werttyp ist Zeichenfolge.

Unterstützte Vorgang ist Get.

<a href="" id="my-wstep"></a>**Meine/WSTEP**  
Erforderlich für Gerät MDM registriert. Der übergeordnete Knoten, der das MDM Registrierung Clientzertifikat hostet bezogene Einstellungen, die über WSTEP registriert ist. Welche Knoten unter WSTEP werden hauptsächlich für Clientzertifikat MDM erneuern Anforderungen. Werttyp ist Knoten.

Unterstützte Vorgang ist Get.

<a href="" id="my-wstep-renew"></a>**Meine/WSTEP/erneuern**  
Optional Der übergeordneten Knoten auf Gruppe Erneuerung bezogene Einstellungen.

Unterstützte Vorgang ist Get.

<a href="" id="my-wstep-renew-serverurl"></a>**Meine/WSTEP/erneuern/ServerURL**  
Optional Gibt die URL des Zertifikatservers Erneuerung. Wenn dieser Knoten nicht vorhanden ist, verwendet der Client die anfängliche Zertifikat Registrierung URL.

> **Hinweis**  Der Erneuerung folgt dieselben Schritte Registrierungsdienst Richtlinie und dann auf Registrierung-Webdienst Gerät Registrierung, d. h., die es mit Discovery-Dienst beginnt gefolgt.

 

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

<a href="" id="my-wstep-renew-renewalperiod"></a>**Meine/WSTEP/erneuern/RenewalPeriod**  
Optional Die Zeit (in Tagen) an den Client initiiert das Clientzertifikat MDM Trigger erneuern Prozess, bevor das MDM Zertifikat abläuft. Der MDM Server kann nicht festgelegt und die Erneuerung Periode aktualisieren. Dieser Parameter gilt für manuelle Zertifikat Erneuerung und Anforderung im Namen (ROBO) Zertifikat Erneuerung. Es wird empfohlen, dass der Zeitraum erneuern einige Monate, bevor das Zertifikat abläuft, um sicherzustellen, dass das Zertifikat mit Datenkonnektivität erfolgreich erneuert ruft festgelegt ist.

Der Standardwert ist 42, und die gültigen Werte lauten 1 – 1000. Werttyp ist eine ganze Zahl.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

> **Hinweis**   Beim Festlegen des Zeitplans Erneuerung SyncML DM Befehle zum ROBOSupport RenewalPeriod und RetryInterval müssen Sie diese in unteilbare Befehle einbinden.

 

<a href="" id="my-wstep-renew-retryinterval"></a>**Meine/WSTEP/erneuern/RetryInterval**  
Optional Gibt das Wiederholungsintervall (in Tagen) bei die vorherige Erneuerung ist fehlgeschlagen. Dies gilt für manuelle Zertifikats Erneuerung und Erneuerung von ROBO automatische Zertifikaten. Der Plan wird an das Zertifikatablaufdatum.

Für ROBO Erneuerung bei einem Ausfall wiederholt der Client die Erneuerung in regelmäßigen Abständen, bis das Gerät Ablaufdatum des Zertifikats erreicht. Dieser Parameter gibt die Wartezeit für ROBO Erneuerung Wiederholungsversuche an.

Bei einem Ausfall manuelle wiederholen stehen keine integrierte Wiederholung. Der Benutzer kann später wiederholen. Bei der nächsten geplanten Zertifikat Erneuerung Retry Periode fordert das Gerät im Dialogfeld Anmeldeinformationen erneut.

Der Standardwert ist 7 und die gültigen Werte lauten 1 – 1000 UND =&lt; RenewalPeriod, andernfalls ihn werden Fehler auftreten. Werttyp ist eine ganze Zahl.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

> **Hinweis**   Wenn Sie den Zeitplan Erneuerung SyncML DM Befehle ROBOSupport, RenewalPeriod und RetryInterval festlegen, müssen Sie diese unteilbare Befehle umschließen.

 

<a href="" id="my-wstep-renew-robosupport"></a>**Meine/WSTEP/erneuern/ROBOSupport**  
Optional Benachrichtigt den Client, wenn der Server MDM Registrierung ROBO automatische Zertifikat Verlängerung unterstützt. Werttyp ist Bool.

ROBO ist die einzige unterstützte Erneuerung-Methode für Windows 10. Dieser Wert wird ignoriert, und immer als true betrachtet.

Unterstützte Vorgänge sind hinzufügen, abrufen, löschen, und ersetzen.

> **Hinweis**   Wenn Sie den Zeitplan Erneuerung SyncML DM Befehle ROBOSupport, RenewalPeriod und RetryInterval festlegen, müssen Sie diese unteilbare Befehle umschließen.

 

<a href="" id="my-wstep-renew-status"></a>**Mein/WSTEP/erneuern/Status**  
Erforderlich. Zeigt den aktuellen Aktionsstatus für dieses Zertifikat. Werttyp ist eine ganze Zahl.

Unterstützte Vorgang ist Get.

Unterstützte Werte sind die folgenden:

-   0 – nicht gestartet.

-   1 – Erneuerung ausgeführt.

-   2 – Erneuerung war erfolgreich.

-   3 – Fehler bei der Erneuerung.

<a href="" id="my-wstep-renew-errorcode"></a>**Meine/WSTEP/erneuern/ErrorCode**  
Optional Wenn Erneuerung von Zertifikaten fehlschlägt, gibt diese Ganzzahlwert HRESULT des letzten Fehlercodes während der Erneuerung an. Werttyp ist eine ganze Zahl.

Unterstützte Vorgang ist Get.

<a href="" id="my-wstep-renew-lastrenewalattempttime"></a>**Meine/WSTEP/erneuern/LastRenewalAttemptTime**  
In Windows 10, Version 1607 hinzugefügt. Zeitpunkt der letzten versuchte Verlängerung.

Unterstützte Vorgang ist Get.

<a href="" id="my-wstep-renew-renewnow"></a>**Meine/WSTEP/erneuern/RenewNow**  
In Windows 10, Version 1607 hinzugefügt. Eine Erneuerung initiiert jetzt.

Unterstützte Vorgang ist ausführen.

## <a name="examples"></a>Beispiele


Fügen Sie ein Stammzertifikat an den MDM Server.

``` syntax
<Add>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>
./Vendor/MSFT/CertificateStore/Root/System/<CertificateHashInsertedhere>/EncodedCertificate
          </LocURI>
      </Target>
      <Data>B64EncodedCertInsertedHere</Data>
      <Meta>
         <Format xmlns="syncml:metinf">b64</Format>
      </Meta>
   </Item>
</Add>
```

Allen installierten Client Zertifikate anfordern.

``` syntax
<Get>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>
./Vendor/MSFT/CertificateStore/My/User?list=StructData
          </LocURI>
      </Target>
   </Item>
</Get>
```

Löschen Sie ein Stammzertifikat.

``` syntax
<Delete>
   <CmdID>1</CmdID>
   <Item>
      <Target>
         <LocURI>
./Vendor/MSFT/CertificateStore/Root/System/<CertificateHashInsertedHere>
          </LocURI>
      </Target>
   </Item>
</Delete>
```

Konfigurieren Sie das Gerät, um ein Clientzertifikat über SCEP registrieren.

``` syntax
<Atomic>
<CmdID>100</CmdID>
<Add>
   <CmdID>1</CmdID>
   <Item>
        <Target><LocURI>./Vendor/MSFT/CertificateStore/My/SCEP/CertSCEP1</LocURI>
        </Target>
        <Meta>
        <Format xmlns="syncml:metinf">node</Format>
        </Meta>
   </Item>
</Add>
<Add>
    <CmdID>2</CmdID>
    <Item>
        <Target><LocURI>./Vendor/MSFT/CertificateStore/My/SCEP/CertSCEP1/Install/RetryCount</LocURI>
        </Target>
    <Meta>
               <Format xmlns="syncml:metinf">int</Format>
    </Meta>
            <Data>1</Data>
    </Item>
</Add>
<Add>
         <CmdID>3</CmdID>
         <Item>
            <Target><LocURI>./Vendor/MSFT/CertificateStore/My/SCEP/CertSCEP1/Install/RetryDelay</LocURI>
            </Target>
            <Meta>
               <Format xmlns="syncml:metinf">int</Format>
            </Meta>
            <Data>1</Data>
         </Item>
</Add>
<Add>
         <CmdID>4</CmdID>
         <Item>
            <Target><LocURI>./Vendor/MSFT/CertificateStore/My/SCEP/CertSCEP1/Install/KeyUsage</LocURI>
            </Target>
            <Meta>
               <Format xmlns="syncml:metinf">int</Format>
            </Meta>
            <Data>160</Data>
         </Item>
</Add>
<Add>
         <CmdID>5</CmdID>
         <Item>
            <Target><LocURI>./Vendor/MSFT/CertificateStore/My/SCEP/CertSCEP1/Install/KeyLength</LocURI>
            </Target>
            <Meta>
               <Format xmlns="syncml:metinf">int</Format>
            </Meta>
            <Data>1024</Data>
         </Item>
</Add>
<Add>
         <CmdID>6</CmdID>
         <Item>
            <Target><LocURI>./Vendor/MSFT/CertificateStore/My/SCEP/CertSCEP1/Install/HashAlgorithm</LocURI>
            </Target>
            <Meta>
               <Format xmlns="syncml:metinf">chr</Format>
            </Meta>
            <Data>SHA-1</Data>
         </Item>
</Add>
<Add>
         <CmdID>7</CmdID>
         <Item>
            <Target><LocURI>./Vendor/MSFT/CertificateStore/My/SCEP/CertSCEP1/Install/SubjectName</LocURI>
            </Target>
            <Meta>
               <Format xmlns="syncml:metinf">chr</Format>
            </Meta>
            <Data>CN=AnnaLee</Data>
         </Item>
</Add>
<Add>
         <CmdID>8</CmdID>
         <Item>
            <Target><LocURI>./Vendor/MSFT/CertificateStore/My/SCEP/CertSCEP1/Install/SubjectAlternativeNames</LocURI>
            </Target>
            <Meta>
               <Format xmlns="syncml:metinf">chr</Format>
            </Meta>
            <Data>11+tom@MyDomain.Contoso.com;3+MyDomain.Contoso.com</Data>
         </Item>
</Add>
<Add>
         <CmdID>9</CmdID>
         <Item>
            <Target><LocURI>./Vendor/MSFT/CertificateStore/My/SCEP/CertSCEP1/Install/ValidPeriod</LocURI>
            </Target>
            <Meta>
               <Format xmlns="syncml:metinf">chr</Format>
            </Meta>
            <Data>Years</Data>
         </Item>
</Add>
<Add>
         <CmdID>10</CmdID>
         <Item>
            <Target><LocURI>./Vendor/MSFT/CertificateStore/My/SCEP/CertSCEP1/Install/ValidPeriodUnits</LocURI>
            </Target>
            <Meta>
               <Format xmlns="syncml:metinf">int</Format>
            </Meta>
            <Data>1</Data>
         </Item>
</Add>
<Add>
         <CmdID>11</CmdID>
         <Item>
            <Target><LocURI>./Vendor/MSFT/CertificateStore/My/SCEP/CertSCEP1/Install/EKUMapping</LocURI>
            </Target>
            <Meta>
               <Format xmlns="syncml:metinf">chr</Format>
            </Meta>
            <Data>1.3.6.1.4.1.311.10.3.12+1.3.6.1.4.1.311.10.3.4+1.3.6.1.4.1.311.20.2.2</Data>
         </Item>
</Add>
<Add>
         <CmdID>12</CmdID>
         <Item>
            <Target><LocURI>./Vendor/MSFT/CertificateStore/My/SCEP/CertSCEP1/Install/KeyProtection</LocURI>
            </Target>
            <Meta>
               <Format xmlns="syncml:metinf">int</Format>
            </Meta>
            <Data>3</Data>
         </Item>
</Add>
<Add>
         <CmdID>13</CmdID>
         <Item>
            <Target><LocURI>./Vendor/MSFT/CertificateStore/My/SCEP/CertSCEP1/Install/ServerURL</LocURI>
            </Target>
            <Meta>
               <Format xmlns="syncml:metinf">chr</Format>
            </Meta>
            <Data>https://contoso.com/certsrv/ctcep.dll</Data>
         </Item>
</Add>
<Add>
         <CmdID>14</CmdID>
         <Item>
            <Target><LocURI>./Vendor/MSFT/CertificateStore/My/SCEP/CertSCEP1/Install/Challenge</LocURI>
            </Target>
            <Meta>
               <Format xmlns="syncml:metinf">chr</Format>
            </Meta>
            <Data>ChallengeInsertedHere</Data>
         </Item>
</Add>
<Add>
         <CmdID>15</CmdID>
         <Item>
            <Target><LocURI>./Vendor/MSFT/CertificateStore/My/SCEP/CertSCEP1/Install/CAThumbprint</LocURI>
            </Target>
            <Meta>
               <Format xmlns="syncml:metinf">chr</Format>
            </Meta>
            <Data>CAThumbprintInsertedHere</Data>
         </Item>
</Add>
<Exec>
         <CmdID>16</CmdID>
         <Item>
            <Target><LocURI>./Vendor/MSFT/CertificateStore/My/SCEP/CertSCEP1/Install/Enroll</LocURI>
            </Target>
         </Item>
</Exec>
</Atomic>
```

Konfigurieren Sie das Gerät, um ein Clientzertifikat MDM mit dem angegebenen automatisch erneuern Punkt und "Wiederholen" Intervall erneuern.

``` syntax
<Atomic>
   <CmdID>1</CmdID>
     <Replace>
         <CmdID>2</CmdID>
         <Item>
            <Target><LocURI>./Vendor/MSFT/CertificateStore/My/WSTEP/Renew/ROBOSupport</LocURI></Target>
            <Meta>
               <Format xmlns="syncml:metinf">bool</Format>
            </Meta>
            <Data>true</Data>
         </Item>
      </Replace>
      <Replace>
         <CmdID>3</CmdID>
         <Item>
            <Target><LocURI>./Vendor/MSFT/CertificateStore/My/WSTEP/Renew/RenewPeriod</LocURI></Target>
            <Meta>
               <Format xmlns="syncml:metinf">int</Format>
            </Meta>
            <Data>60</Data>
         </Item>
      </Replace>
      <Replace>
         <CmdID>4</CmdID>
         <Item>
            <Target><LocURI>./Vendor/MSFT/CertificateStore/My/WSTEP/Renew/RetryInterval</LocURI></Target>
            <Meta>
               <Format xmlns="syncml:metinf">int</Format>
            </Meta>
            <Data>4</Data>
         </Item>
      </Replace>
</Atomic>
```

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






