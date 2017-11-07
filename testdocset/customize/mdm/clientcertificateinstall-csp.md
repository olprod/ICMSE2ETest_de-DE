---
title: ClientCertificateInstall CSP
description: ClientCertificateInstall CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: B624EB73-2972-47F2-9D7E-826D641BF8A7
ms.openlocfilehash: dd43ed8e3f17a2c9439b01748cf968187a693ea7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="clientcertificateinstall-csp"></a>ClientCertificateInstall CSP


ClientCertificateInstall Konfigurationsdienstanbieter ermöglicht das Unternehmen so installieren Sie Clientzertifikate an.

PFX-Zertifikat installieren und SCEP Installation müssen die Befehle SyncML umgebrochen in unteilbare Befehle aus, um sicherzustellen, dass die Ausführung der Registrierung nicht ausgelöst wird, bis alle Einstellungen konfiguriert sind. Der Befehl registrieren muss das letzte Element in der unteilbare blockieren.

> **Hinweis**  
Derzeit Windows 10, Version 1511, wann sind Zertifikate auf dem Gerätespeicher und der Benutzerspeicher und beide Zertifikate installieren mithilfe der ClientCertificateInstall gesendet, um das Gerät in der gleichen MDM Nutzlast im Benutzerspeicher auch das Zertifikat für die direkte Verwendung für den Gerätespeicher installiert wird. Dadurch verursacht möglicherweise Probleme mit Wi-Fi oder VPN-Wenn Sie das richtige Zertifikat zum Herstellen einer Verbindung auswählen. Wir arbeiten um dieses Problem zu beheben.

Sie können nur auf true, wenn PFXKeyExportable festlegen KeyLocation = 3. CSP schlägt fehl, für alle anderen KeyLocation-Werte.


Die folgende Abbildung zeigt den ClientCertificateInstall Konfiguration-Dienstanbieter in der Strukturformat.

![Clientcertificateinstall csp](images/provisioning-csp-clientcertificateinstall.png)

<a href="" id="device-or-user"></a>**Gerät oder Benutzer**  
<p style="margin-left: 20px">Verwenden Sie für Device-Zertifikate **./Device/Vendor/MSFT** Pfad und für Benutzerzertifikate **./User/Vendor/MSFT** Pfad.

<a href="" id="clientcertificateinstall"></a>**ClientCertificateInstall**  
<p style="margin-left: 20px">Der Stammknoten für den Dienstanbieter für ClientCertificateInstaller-Konfiguration.

<a href="" id="clientcertificateinstall-pfxcertinstall"></a>**ClientCertificateInstall/PFXCertInstall**  
<p style="margin-left: 20px">Für die Installation der PFX-Zertifikat erforderlich. Der übergeordnete Knoten das PFX-Zertifikat gruppieren bezogene Einstellungen.

<p style="margin-left: 20px">Unterstützte Vorgang ist Get.

<a href="" id="clientcertificateinstall-pfxcertinstall-uniqueid"></a>**ClientCertificateInstall/PFXCertInstall / ***_UniqueID_**  
<p style="margin-left: 20px">Erforderlich für PFX-Zertifikat installieren. Eine eindeutige ID zur Unterscheidung von anderen Zertifikats installieren Anforderungen.

<p style="margin-left: 20px">Das Typ-Datenformat ist Knoten.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Get, hinzufügen und löschen.

<p style="margin-left: 20px">Durch Aufrufen löschen auf diesem Knoten sollte gelöscht, die Zertifikate und die Schlüssel, die von den entsprechenden PFX Blob installiert wurden.

<a href="" id="clientcertificateinstall-pfxcertinstall-uniqueid-keylocation"></a>* *ClientCertificateInstall/PFXCertInstall/*UniqueID*/KeyLocation**
<p style="margin-left: 20px">Erforderlich für PFX-Zertifikat installieren. Gibt an, den KeyStorage Anbieter zu adressieren die private Schlüssel Installation.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Get, hinzufügen, und ersetzen.

<p style="margin-left: 20px">Der Datentyp ist eine ganze Zahl, die einen der folgenden Werte:

| Wert | Beschreibung                                                                                                   |
|-------|---------------------------------------------------------------------------------------------------------------|
| 1     | An TPM installieren, sofern vorhanden, ein Fehler auftritt, wenn nicht vorhanden.                                                               |
| 2     | Installieren Sie auf TPM, sofern vorhanden. Wenn nicht vorhanden ist, auf die Software zurückgegriffen.                                              |
| 3     | Installieren Sie auf Software.                                                                                          |
| 4     | Installieren von Windows Hello für Unternehmen (vormals Microsoft Passport für Arbeit), dessen Name angegeben wird |


<a href="" id="clientcertificateinstall-pfxcertinstall-uniqueid-containername"></a>* *ClientCertificateInstall/PFXCertInstall/*UniqueID*/ContainerName**  
<p style="margin-left: 20px">Ptional. Gibt die Windows Hello für Firmenname (vormals Microsoft Passport für die Arbeit) Container (sofern Windows Hello für Business Speicheranbieter (KSP) für die KeyLocation ausgewählt ist). Registrierung schlägt fehl, wenn dieser Knoten nicht angegeben wird Wenn Windows Hello für Business KSP ausgewählt ist.

<p style="margin-left: 20px">Date-Typ ist Zeichenfolge.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Get, hinzufügen, und ersetzen.

<a href="" id="clientcertificateinstall-pfxcertinstall-uniqueid-pfxcertblob"></a>* *ClientCertificateInstall/PFXCertInstall/*UniqueID*/PFXCertBlob**
<p style="margin-left: 20px">CRYPT\_DATEN\_BLOB-Struktur, die ein PFX-Paket mit der exportierten und verschlüsselte Zertifikate und Schlüssel enthält. Das Hinzufügen eines Elements löst das Hinzufügen der PFX-Zertifikat aus. Dies erfordert, dass alle anderen Knoten unter UniqueID, die Parameter für die PFX-Installation (Container Name, KeyLocation, CertPassword, KeyExportable) sind sind vorhanden, bevor er aufgerufen wird. Hierdurch wird den Status Knoten auch auf den aktuellen Status des Vorgangs.

<p style="margin-left: 20px">Das Typ-Datenformat ist binär.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Get, hinzufügen, und ersetzen.

<p style="margin-left: 20px">Wenn ein Blob bereits vorhanden ist, schlägt das Hinzufügen eines Elements fehl. Wenn ersetzen auf diesem Knoten aufgerufen wird, werden die vorhandenen Zertifikate überschrieben.

<p style="margin-left: 20px">Wenn hinzufügen auf diesem Knoten für eine neue PFX aufgerufen wird, wird das Zertifikat hinzugefügt werden. Wenn ein Zertifikat nicht vorhanden ist, schlägt fehl, Ersetzungsvorgang auf diesem Knoten.

<p style="margin-left: 20px">Anders ausgedrückt, mit ersetzen oder hinzufügen, bewirken die Auswirkung des entweder das alte Zertifikat überschreiben oder Hinzufügen eines neuen Zertifikats CRYPT\_DATEN\_BLOB, die in nachlesen können [CRYPT\_ganze ZAHL\_BLOB](http://go.microsoft.com/fwlink/p/?LinkId=523871).

<a href="" id="clientcertificateinstall-pfxcertinstall-uniqueid-pfxcertpassword"></a>* *ClientCertificateInstall/PFXCertInstall/*UniqueID*/PFXCertPassword**
<p style="margin-left: 20px">Kennwort, das den Blob PFX schützt. Dies ist erforderlich, wenn die PFX ein Kennwort geschützt ist.

<p style="margin-left: 20px">Datentyp ist eine Zeichenfolge.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Get, hinzufügen, und ersetzen.

<a href="" id="clientcertificateinstall-pfxcertinstall-uniqueid-pfxcertpasswordencryptiontype"></a>* *ClientCertificateInstall/PFXCertInstall/*UniqueID*/PFXCertPasswordEncryptionType**
<p style="margin-left: 20px">Optional Hiermit geben Sie an das Kennwort der PFX-Zertifikat wird mit dem Zertifikat MDM die MDM verschlüsselt Whtether Server.

<p style="margin-left: 20px">Der Datentyp ist "int" Gültige Werte:

-   0 – ist das Kennwort nicht verschlüsselt.
-   1 – Kennwort wird mit dem MDM-Zertifikat verschlüsselt.
-   2 - Kennwort wird mit benutzerdefinierten-Zertifikat verschlüsselt.

<p style="margin-left: 20px">Wenn PFXCertPasswordEncryptionType = 2, geben Sie den Namen des Store in PFXCertPasswordEncryptionStore-Einstellung.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Get, hinzufügen, und ersetzen.

<a href="" id="clientcertificateinstall-pfxcertinstall-uniqueid-pfxkeyexportable"></a>* *ClientCertificateInstall/PFXCertInstall/*UniqueID*/PFXKeyExportable**
<p style="margin-left: 20px">Optional Verwendet, um anzugeben, ob der private Schlüssel installiert exportierbar ist (und höher exportiert werden können). Die PFX ist nicht "Exportierbar" markieren, wenn es an TPM installiert ist.

> **Hinweis**  Sie können nur auf true, wenn PFXKeyExportable festlegen KeyLocation = 3. Der CSP schlägt fehl, für alle anderen KeyLocation-Werte.

 
<p style="margin-left: 20px">Der Bool-Datentyp.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Get, hinzufügen, und ersetzen.

<a href="" id="clientcertificateinstall-pfxcertinstall-uniqueid-thumbprint"></a>* *ClientCertificateInstall/PFXCertInstall/*UniqueID*/Thumbprint**
<p style="margin-left: 20px">Gibt den Fingerabdruck des installierten PFX-Zertifikat zurück.

<p style="margin-left: 20px">Der Datentyp ist eine Zeichenfolge.

<p style="margin-left: 20px">Unterstützte Vorgang ist Get.

<a href="" id="clientcertificateinstall-pfxcertinstall-uniqueid-status"></a>* *ClientCertificateInstall/PFXCertInstall/*UniqueID*/Status**
<p style="margin-left: 20px">Erforderlich. Gibt den Fehlercode des PFX-Installation aus den GetLastError Befehl aufgerufen, nachdem der PfxImportCertStore zurück.

<p style="margin-left: 20px">Datentyp ist eine ganze Zahl.

<p style="margin-left: 20px">Unterstützte Vorgang ist Get.

<a href="" id="clientcertificateinstall-pfxcertinstall-uniqueid-pfxcertpasswordencryptionstore"></a>* *ClientCertificateInstall/PFXCertInstall/*UniqueID*/PFXCertPasswordEncryptionStore**
<p style="margin-left: 20px">In Windows 10, Version 1511 hinzugefügt. Wenn PFXCertPasswordEncryptionType = 2, gibt den Speichernamen des Zertifikats für die Entschlüsselung der PFXCertPassword verwendet.

<p style="margin-left: 20px">Datentyp ist Zeichenfolge.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="clientcertificateinstall-scep"></a>**ClientCertificateInstall/SCEP**  
<p style="margin-left: 20px">Der Knoten für SCEP.

> **Hinweis**  Eine Benachrichtigung wird gesendet, nachdem das Zertifikat SCEP installiert ist.

 
<a href="" id="clientcertificateinstall-scep-uniqueid"></a>**ClientCertificateInstall/SCEP / ***_UniqueID_**  
<p style="margin-left: 20px">Eine eindeutige ID auf anderes Zertifikat Installation Anfragen zu unterscheiden.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

<a href="" id="clientcertificateinstall-scep-uniqueid-install"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/Install**
<p style="margin-left: 20px">Ein Knoten für die Registrierung von Zertifikaten SCEP erforderlich. Übergeordneten Knoten auf Gruppe SCEP Cert Installation weiterführende Anforderungen.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Get, hinzufügen, ersetzen und löschen.

> **Hinweis**  Obwohl die untergeordneten Knoten unter Install Support ersetzen dauert Befehle, nachdem der Befehl Exec an das Gerät, das Gerät gesendet wird die Werte festgelegt sind, wenn der Befehl Exec akzeptiert wird. Der Server erwarten nicht die Änderung des Werts Knoten, nachdem Befehl Exec zugestimmt haben, wie es die aktuelle Registrierung entwickelten auswirkt. Der Server sollte überprüfen Sie den Wert der Status-Knoten, und stellen Sie sicher, dass das Gerät vor dem Ändern der Werte von untergeordneten Knoten nicht an einem unbekannten Zustand befindet.

 
<a href="" id="clientcertificateinstall-scep-uniqueid-install-serverurl"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/Install/ServerURL **  
<p style="margin-left: 20px">Für die Registrierung von Zertifikaten SCEP erforderlich. Gibt den Registrierung Zertifikatserver. Mehrere Server URLs können durch Semikolons voneinander getrennt aufgelistet werden.

<p style="margin-left: 20px">Datentyp ist Zeichenfolge.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Get, hinzufügen, und ersetzen.

<a href="" id="clientcertificateinstall-scep-uniqueid-install-challenge"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/Install/Herausforderung **
<p style="margin-left: 20px">Für die Registrierung von Zertifikaten SCEP erforderlich. B64 codiert SCEP Registrierung Herausforderung. Herausforderung wird gelöscht, kurz nachdem Sie der Befehl Exec zugestimmt haben.

<p style="margin-left: 20px">Datentyp ist Zeichenfolge.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="clientcertificateinstall-scep-uniqueid-install-ekumapping"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/Install/EKUMapping **
<p style="margin-left: 20px">Erforderlich. Gibt die erweiterte Schlüsselverwendung. Betreff zu SCEP Serverkonfiguration. Die Liste der OIDs werden getrennt durch ein Pluszeichen **+**. Beispielsweise *OID1*+*OID2*+*OID3*.

Datentyp ist Zeichenfolge.
<p style="margin-left: 20px">Für die Registrierung erforderlich. Gibt die Enhanced Key Usage Bits (0 x 80, 0 x 20, 0xA0, usw.) für das Zertifikat im Dezimalformat. Der Wert sollte mindestens die zweite (0 x 20), 4 (0 x 80) oder beide Bits festgelegt. Die Konfiguration schlägt fehl, wenn der Wert diese Bits festgelegt hat.

<p style="margin-left: 20px">Datentyp ist int

<p style="margin-left: 20px">Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="clientcertificateinstall-scep-uniqueid-install-subjectname"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/Install/SubjectName **
<p style="margin-left: 20px">Erforderlich. Gibt den Antragstellernamen an.

<p style="margin-left: 20px">Datentyp ist Zeichenfolge.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="clientcertificateinstall-scep-uniqueid-install-keyprotection"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/Install/KeyProtection **
<p style="margin-left: 20px">Optional Gibt an, wohin den privaten Schlüssel beibehalten.

> **Hinweis**  Selbst wenn der private Schlüssel durch TPM geschützt ist, ist es nicht mit einer PIN TPM geschützt.

 
<p style="margin-left: 20px">Der Datentyp ist eine ganze Zahl, die einen der folgenden Werte:

| Wert | Beschreibung                                                                                                                                                                                           |
|-------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1     | Geschützt durch TPM des privaten Schlüssels.                                                                                                                                                                         |
| 2     | Privaten Schlüssel, die per Telefon TPM geschützt werden, wenn das Gerät TPM unterstützt. Alle Windows Phone 8.1 Geräte unterstützen TPM und 2 Wert als 1 behandelt.                                                                 |
| 3     | (Standard) Privaten Schlüssel in Software KSP gespeichert.                                                                                                                                                          |
| 4     | Privaten Schlüssel durch Windows Hello für Unternehmen (vormals Microsoft Passport für die Arbeit) geschützt werden. Wenn diese Option angegeben wird, muss der ContainerName angegeben, andernfalls Registrierung schlägt fehl. |

 
<p style="margin-left: 20px">Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="clientcertificateinstall-scep-uniqueid-install-retrydelay"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/Install/RetryDelay **
<p style="margin-left: 20px">Optional Wenn der Server SCEP ausstehend sendet, gibt dieser Wert Gerät Retry Wartezeit in Minuten.

<p style="margin-left: 20px">Typ Datenformat ist eine ganze Zahl.

<p style="margin-left: 20px">Der Standardwert ist 5.

<p style="margin-left: 20px">Der Mindestwert ist 1.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="clientcertificateinstall-scep-uniqueid-install-retrycount"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/Install/RetryCount **
<p style="margin-left: 20px">Optional Für SCEP eindeutig. Gibt die Gerät "Wiederholen" Zeiten, wenn der Server SCEP ausstehend sendet.

<p style="margin-left: 20px">Datentyp ist Integer.

<p style="margin-left: 20px">Standardwert ist 3.

<p style="margin-left: 20px">Maximale Wert ist 30. Wenn der Wert größer als 30 ist, wird das Gerät 30 verwenden.

<p style="margin-left: 20px">Mindestwert ist 0 (null) und gibt an, keine wiederholen.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="clientcertificateinstall-scep-uniqueid-install-templatename"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/Install/TemplateName **
<p style="margin-left: 20px">Optional Der Objektbezeichner des Vorlagenname Zertifikat.

> **Hinweis**  Dieser Name wird in der Regel vom Server SCEP ignoriert. aus diesem Grund muss nicht MDM der Server normalerweise bereit.

 
<p style="margin-left: 20px">Datentyp ist Zeichenfolge.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="clientcertificateinstall-scep-uniqueid-install-keylength"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/Install/erkannt wurden **
<p style="margin-left: 20px">Erforderlich für die Registrierung. Geben Sie die Länge des privaten Schlüssels (RSA).

<p style="margin-left: 20px">Datentyp ist Integer.

<p style="margin-left: 20px">Gültige Werte sind 1024, 2048 und 4096.

<p style="margin-left: 20px">Für Windows Hello für Unternehmen (vormals Microsoft Passport für Arbeit) ist nur 2048 die Schlüssellänge unterstützten.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="clientcertificateinstall-scep-uniqueid-install-hashalgorithm"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/Install/HashAlgorithm **
<p style="margin-left: 20px">Erforderlich. Hash-Algorithmus Familie (SHA-1, SHA-2, SHA-3) durch MDM Server angegeben. Wenn mehrere Hash-Algorithmus-Familien angegeben sind, getrennt werden müssen mit **+**.

<p style="margin-left: 20px">Für Windows Hello für Unternehmen wird nur SHA256 unterstützter Algorithmus.

<p style="margin-left: 20px">Datentyp ist Zeichenfolge.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="clientcertificateinstall-scep-uniqueid-install-cathumbprint"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/Install/CAThumbprint **
<p style="margin-left: 20px">Erforderlich. Gibt die Stammzertifizierungsstelle Fingerabdruck an. Dies ist eine 20-Byte-Wert des SHA1 Zertifikathash als ein hexadezimaler Zeichenfolgenwert angegeben. Bei Client der SCEP Server authentifiziert, überprüft das Zertifikat vom Server SCEP eine Übereinstimmung mit diesem Zertifikat überprüfen. Wenn es sich nicht um eine Übereinstimmung ist, schlägt die Authentifizierung fehl.

<p style="margin-left: 20px">Datentyp ist Zeichenfolge.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="clientcertificateinstall-scep-uniqueid-install-subjectalternativenames"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/Install/SubjectAlternativeNames **
<p style="margin-left: 20px">Optional Gibt die alternative Antragstellernamen (SAN). Dieser Knoten können mehrere alternative Namen angegeben werden. Jede Name ist die Kombination aus Namensformat + tatsächlichen Namen. Die Name-Typdefinitionen in MSDN für Weitere Informationen finden Sie unter.

<p style="margin-left: 20px">Jedes Paar wird durch Semikolon getrennt. Beispielsweise werden mehrere SANs im Format bearbeitet * \[Namen format1\]*+*\[tatsächlichen name1\]*; * \[Namensformat 2\] * +*\[actual name2\]*.

<p style="margin-left: 20px">Datentyp ist Zeichenfolge.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="clientcertificateinstall-scep-uniqueid-install-validperiod"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/Install/ValidPeriod **
<p style="margin-left: 20px">Optional Gibt die Einheiten für den Zeitraum gültiges Zertifikat.

<p style="margin-left: 20px">Datentyp ist Zeichenfolge.

<p style="margin-left: 20px">Gültige Werte sind:

-   Tage (Standard)
-   Monate
-   Jahre

> **Hinweis**  Das Gerät sendet MDM Server erwartet Gültigkeitsdauer des Zertifikats (ValidPeriodUnits + ValidPeriod) nur auf dem Server SCEP im Rahmen der Registrierung zertifikatanforderung. Je nach Serverkonfiguration definiert, der Server wie dieser Zeitraum gültig zu verwenden, um das Zertifikat zu erstellen.

 
<p style="margin-left: 20px">Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="clientcertificateinstall-scep-uniqueid-install-validperiodunits"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/Install/ValidPeriodUnits **
<p style="margin-left: 20px">Optional Gibt die gewünschte Anzahl von Einheiten, die in den Gültigkeitszeitraum verwendet. Dies ist SCEP Serverkonfiguration. Standardwert ist 0. Der Einheitentyp (Tage, Monate oder Jahre) sind in der ValidPeriod-Knoten definiert. Beachten Sie, der Gültigkeitszeitraum MDM gemäß den Gültigkeitszeitraum angegeben, in der Zertifikatvorlage überschrieben werden. Beispielsweise bedeutet Wenn ValidPeriod Tage und ValidPeriodUnits 30 ist, dies, dass die gültige Gesamtdauer 30 Tage ist.

<p style="margin-left: 20px">Datentyp ist Zeichenfolge.

>**Hinweis**  Das Gerät sendet nur MDM Server erwartet Gültigkeitsdauer des Zertifikats (ValidPeriodUnits + ValidPeriod) an den SCEP Server als Teil des zertifikatanforderung für die Registrierung. Je nach Serverkonfiguration definiert, der Server wie dieser Zeitraum gültig zu verwenden, um das Zertifikat zu erstellen.

 
<p style="margin-left: 20px">Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="clientcertificateinstall-scep-uniqueid-install-containername"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/Install/ContainerName **
<p style="margin-left: 20px">Optional Gibt an, die Windows Hello für Container Firmenname (Wenn Windows Hello für Business KSP des Knotens ausgewählt ist). Wenn dieser Knoten nicht angegeben wird, wenn Windows Hello für Business KSP ausgewählt ist, schlägt die Registrierung fehl.

<p style="margin-left: 20px">Datentyp ist Zeichenfolge.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="clientcertificateinstall-scep-uniqueid-install-customtexttoshowinprompt"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/Install/CustomTextToShowInPrompt **
<p style="margin-left: 20px">Optional Gibt den benutzerdefinierten Text während der Registrierung von Zertifikaten auf dem Windows Hello Business PIN Aufforderung zum angezeigt. Der Administrator kann wahlweise finden Sie weitere kontextbezogene Informationen in diesem Feld für Warum muss der Benutzer die PIN-NUMMER einzugeben und was das Zertifikat verwendet werden soll.

<p style="margin-left: 20px">Datentyp ist Zeichenfolge.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Add, Get, und Ersetzen Sie.

<a href="" id="clientcertificateinstall-scep-uniqueid-install-enroll"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/installieren/registrieren **
<p style="margin-left: 20px">Erforderlich. Löst das Gerät, um die Registrierung von Zertifikaten zu starten. Das Gerät wird nicht MDM Server benachrichtigen Sie nach Abschluss der Registrierung von Zertifikaten. Der MDM Server konnte später Abfragen des Geräts, um herauszufinden, ob ein neues Zertifikat hinzugefügt wird.

<p style="margin-left: 20px">Das Datumsformat Typ ist Null, was bedeutet, dass dieser Knoten keinen Wert enthält.

<p style="margin-left: 20px">Der einzige unterstützte Vorgang ist ausführen.

<a href="" id="clientcertificateinstall-scep-uniqueid-certthumbprint"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/CertThumbprint**
<p style="margin-left: 20px">Optional Gibt das aktuelle Zertifikat Fingerabdruck erfolgreicher Registrierung von Zertifikaten. Es ist ein 20-Byte-Wert des angegebenen als ein hexadezimaler Zeichenfolgenwert SHA1 Zertifikat-Hash.

<p style="margin-left: 20px">Wenn das Zertifikat auf dem Gerät ungültig wird (Zertifikat abgelaufen, Zertifikatskette ist nicht gültig, der private Schlüssel gelöscht) sie eine leere Zeichenfolge zurück.

<p style="margin-left: 20px">Datentyp ist Zeichenfolge.

<p style="margin-left: 20px">Der einzige unterstützte Vorgang ist Get.

<a href="" id="clientcertificateinstall-scep-uniqueid-status"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/Status**
<p style="margin-left: 20px">Erforderlich. Neueste Status der zertifizierten während der Registrierung Anforderung angegeben.

<p style="margin-left: 20px">Datentyp ist Zeichenfolge. Gültige Werte:

<p style="margin-left: 20px">Der einzige unterstützte Vorgang ist Get.

| Wert | Beschreibung                                                                                       |
|-------|---------------------------------------------------------------------------------------------------|
| 1     | Erfolgreich fertig gestellt                                                                             |
| 2     | Ausstehende (das Gerät noch nicht abgeschlossen ist die Aktion, aber den Server SCEP ausstehende Antwort erhalten hat) |
| 16    | Aktion ist fehlgeschlagen                                                                                     |
| 32    | Unbekannt                                                                                           |

 
<a href="" id="clientcertificateinstall-scep-uniqueid-errorcode"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/ErrorCode**  
<p style="margin-left: 20px">Optional Ein Ganzzahlwert, der angibt, das HRESULT des letzten Registrierung Fehlercodes.

<p style="margin-left: 20px">Der einzige unterstützte Vorgang ist Get.

<a href="" id="clientcertificateinstall-scep-uniqueid-respondentserverurl"></a>* *ClientCertificateInstall/SCEP/*UniqueID*/RespondentServerUrl**
<p style="margin-left: 20px">Erforderlich. Gibt die URL des Servers SCEP, die auf die Registrierung-Anforderung reagiert.

<p style="margin-left: 20px">Datentyp ist Zeichenfolge.

<p style="margin-left: 20px">Der einzige unterstützte Vorgang ist Get.

## <a name="example"></a>Beispiel


Registrieren Sie ein Clientzertifikat über SCEP an.

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Atomic>
        <Add>
            <CmdID>301</CmdID>
            <Item>
                <Target>
                    <LocURI>./Device/Vendor/MSFT/ClientCertificateInstall/SCEP/<InsertUniqueIDHere></LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">node</Format>
                </Meta>
            </Item>
        </Add>
        <Add>
            <CmdID>302</CmdID>
            <Item>
                <Target>
                    <LocURI>./Device/Vendor/MSFT/ClientCertificateInstall/SCEP/<InsertUniqueIDHere>/Install/RetryCount</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">int</Format>
                </Meta>
                <Data>1</Data>
            </Item>
        </Add>
        <Add>
            <CmdID>303</CmdID>
            <Item>
                <Target>
                    <LocURI>./Device/Vendor/MSFT/ClientCertificateInstall/SCEP/<InsertUniqueIDHere>/Install/RetryDelay</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">int</Format>
                </Meta>
                <Data>1</Data>
            </Item>
        </Add>
        <Add>
            <CmdID>304</CmdID>
            <Item>
                <Target>
                    <LocURI>./Device/Vendor/MSFT/ClientCertificateInstall/SCEP/<InsertUniqueIDHere>/Install/KeyUsage</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">int</Format>
                </Meta>
                <Data>160</Data>
            </Item>
        </Add>
        <Add>
            <CmdID>305</CmdID>
            <Item>
                <Target>
                    <LocURI>./Device/Vendor/MSFT/ClientCertificateInstall/SCEP/<InsertUniqueIDHere>/Install/KeyLength</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">int</Format>
                </Meta>
                <Data>1024</Data>
            </Item>
        </Add>
        <Add>
            <CmdID>306</CmdID>
            <Item>
                <Target>
                    <LocURI>./Device/Vendor/MSFT/ClientCertificateInstall/SCEP/<InsertUniqueIDHere>/Install/HashAlgorithm</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">chr</Format>
                </Meta>
                <Data>SHA-1</Data>
            </Item>
        </Add>
        <Add>
            <CmdID>307</CmdID>
            <Item>
                <Target>
                    <LocURI>./Device/Vendor/MSFT/ClientCertificateInstall/SCEP/<InsertUniqueIDHere>/Install/SubjectName</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">chr</Format>
                </Meta>
                <Data>CN=ContosoCSP</Data>
            </Item>
        </Add>
        <Add>
            <CmdID>308</CmdID>
            <Item>
                <Target>
                    <LocURI>./Device/Vendor/MSFT/ClientCertificateInstall/SCEP/<InsertUniqueIDHere>/Install/SubjectAlternativeNames</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">chr</Format>
                </Meta>
                <Data></Data>
            </Item>
        </Add>
        <Add>
            <CmdID>309</CmdID>
            <Item>
                <Target>
                    <LocURI>./Device/Vendor/MSFT/ClientCertificateInstall/SCEP/<InsertUniqueIDHere>/Install/ValidPeriod</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">chr</Format>
                </Meta>
                <Data>Years</Data>
            </Item>
        </Add>
        <Add>
            <CmdID>310</CmdID>
            <Item>
                <Target>
                    <LocURI>./Device/Vendor/MSFT/ClientCertificateInstall/SCEP/<InsertUniqueIDHere>/Install/ValidPeriodUnits</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">int</Format>
                </Meta>
                <Data>1</Data>
            </Item>
        </Add>
        <Add>
            <CmdID>311</CmdID>
            <Item>
                <Target>
                    <LocURI>./Device/Vendor/MSFT/ClientCertificateInstall/SCEP/<InsertUniqueIDHere>/Install/EKUMapping</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">chr</Format>
                </Meta>
                <Data>1.3.6.1.4.1.311.10.3.12+1.3.6.1.4.1.311.10.3.4+1.3.6.1.4.1.311.20.2.2+1.3.6.1.5.5.7.3.2</Data>
            </Item>
        </Add>
        <Add>
            <CmdID>312</CmdID>
            <Item>
                <Target>
                    <LocURI>./Device/Vendor/MSFT/ClientCertificateInstall/SCEP/<InsertUniqueIDHere>/Install/KeyProtection</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">int</Format>
                </Meta>
                <Data>3</Data>
            </Item>
        </Add>
        <Add>
            <CmdID>313$</CmdID>
            <Item>
                <Target>
                    <LocURI>./Device/Vendor/MSFT/ClientCertificateInstall/SCEP/<InsertUniqueIDHere>/Install/ServerURL</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">chr</Format>
                </Meta>
                <Data>http://constoso.com/certsrv/mscep/mscep.dll</Data>
            </Item>
        </Add>
        <Add>
            <CmdID>314</CmdID>
            <Item>
                <Target>
                    <LocURI>./Device/Vendor/MSFT/ClientCertificateInstall/SCEP/<InsertUniqueIDHere>/Install/Challenge</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">chr</Format>
                </Meta>
                <Data>1234CB055B7EBF384A9486A22B7559A5</Data>
            </Item>
        </Add>
        <Add>
            <CmdID>315</CmdID>
            <Item>
                <Target>
                    <LocURI>./Device/Vendor/MSFT/ClientCertificateInstall/SCEP/<InsertUniqueIDHere>/Install/CAThumbprint</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">chr</Format>
                </Meta>
                <Data>12345087E648875D1DF5D9F9FF89DD10</Data>
            </Item>
        </Add>
        <Exec>
            <CmdID>316</CmdID>
            <Item>
                <Target>
                    <LocURI>./Device/Vendor/MSFT/ClientCertificateInstall/SCEP/<InsertUniqueIDHere>/Install/Enroll</LocURI>
                </Target>
            </Item>
        </Exec>
        </Atomic>  
        <Final/>
    </SyncBody>
</SyncML>
```

Fügen Sie eine PFX-Zertifikat. Das Kennwort der PFX-Zertifikat ist mit einem benutzerdefinierten verschlüsselt Zertifikatspeicher für "My".

``` syntax
<SyncML>
    <SyncBody>
            <Delete>
                <CmdID>$CmdID$</CmdID>
                <Item>
                    <Target>
                        <LocURI>./User/Vendor/MSFT/ClientCertificateInstall/PFXCertInstall/813A171D7341E1DA90D4A01878DD5328D351900C</LocURI>
                    </Target>
                </Item>
            </Delete>
        <Atomic>
            <CmdID>$CmdID$</CmdID>
            <Add>
                <CmdID>$CmdID$</CmdID>
                <Item>
                    <Target>
                        <LocURI>./User/Vendor/MSFT/ClientCertificateInstall/PFXCertInstall/813A171D7341E1DA90D4A01878DD5328D351900C/KeyLocation</LocURI>
                    </Target>
                    <Meta>
                        <Format xmlns="syncml:metinf">int</Format>
                    </Meta>
                    <Data>2</Data>
                </Item>
            </Add>
            <Add>
                <CmdID>$CmdID$</CmdID>
                <Item>
                    <Target>
                        <LocURI>./User/Vendor/MSFT/ClientCertificateInstall/PFXCertInstall/813A171D7341E1DA90D4A01878DD5328D351900C/PFXCertBlob</LocURI>
                    </Target>
                     <Meta>
                        <Format xmlns="syncml:metinf">chr</Format>
                    </Meta>
                    <Data>Base64_Encode_Cert_Blob</Data>
                </Item>
            </Add>
            <Add>
                <CmdID>$CmdID$</CmdID>
                <Item>
                    <Target>
                        <LocURI>./User/Vendor/MSFT/ClientCertificateInstall/PFXCertInstall/813A171D7341E1DA90D4A01878DD5328D351900C/PFXCertPassword</LocURI>
                    </Target>
                     <Meta>
                        <Format xmlns="syncml:metinf">chr</Format>
                    </Meta>
                    <Data>Base64Encoded_Encrypted_Password_Blog</Data>
                </Item>
            </Add>   
            <Add>
                <CmdID>$CmdID$</CmdID>
                <Item>
                    <Target>
                        <LocURI>./User/Vendor/MSFT/ClientCertificateInstall/PFXCertInstall/813A171D7341E1DA90D4A01878DD5328D351900C/PFXCertPasswordEncryptionType</LocURI>
                    </Target>
                    <Meta>
                        <Format xmlns="syncml:metinf">int</Format>
                    </Meta>
                    <Data>2</Data>
                </Item>
            </Add>     
            <Add>
                <CmdID>$CmdID$</CmdID>
                <Item>
                    <Target>
                        <LocURI>./User/Vendor/MSFT/ClientCertificateInstall/PFXCertInstall/813A171D7341E1DA90D4A01878DD5328D351900C/PFXCertPasswordEncryptionStore</LocURI>
                    </Target>
                    <Meta>
                        <Format xmlns="syncml:metinf">chr</Format>
                    </Meta>
                    <Data>My</Data>
                </Item>
            </Add>     

            <Add>
                <CmdID>$CmdID$</CmdID>
                <Item>
                    <Target>
                        <LocURI>./User/Vendor/MSFT/ClientCertificateInstall/PFXCertInstall/813A171D7341E1DA90D4A01878DD5328D351900C/PFXKeyExportable</LocURI>
                    </Target>
                    <Meta>
                        <Format xmlns="syncml:metinf">bool</Format>
                    </Meta>
                    <Data>true</Data>
                </Item>
            </Add>
        </Atomic>
    <Final/>
    </SyncBody>
</SyncML>
```

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






