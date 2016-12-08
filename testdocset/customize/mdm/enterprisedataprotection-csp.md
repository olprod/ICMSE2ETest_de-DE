---
title: EnterpriseDataProtection CSP
description: Der EnterpriseDataProtection Konfiguration-Dienstanbieter (CSP) wird verwendet, um die Windows-Schutz (WIP) (vormals Enterprise Data Protection) spezielle Einstellungen konfigurieren.
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: E2D4467F-A154-4C00-9208-7798EF3E25B3
ms.openlocfilehash: c0690f2f1f0b226061f928906a0e79aa4136a760
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enterprisedataprotection-csp"></a>EnterpriseDataProtection CSP


Der EnterpriseDataProtection Konfiguration-Dienstanbieter (CSP) wird verwendet, um spezielle Einstellungen der Windows-Schutz (WIP) (vormals Enterprise Data Protection) konfigurieren. Weitere Informationen zu WIP finden Sie unter [Schützen Sie Ihre Enterprise-Daten mithilfe von Windows Informationen Schutz (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).

> **Hinweis**  
>- Um WIP AppLocker CSP und die Netzwerk-Isolation spezifischen Einstellungen funktionsfähig machen muss auch konfiguriert werden. Weitere Informationen finden Sie unter [AppLocker CSP](applocker-csp.md) und NetworkIsolation Richtlinien im [Bereich CSP Richtlinie](policy-configuration-service-provider.md).
>- Dieser CSP wurde in Windows 10, Version 1607 hinzugefügt.

 

Während WIP keine harte Abhängigkeit VPN aufweist, sollte die besten Ergebnisse erzielen Sie VPN-Profile zuerst konfigurieren vor dem Konfigurieren von Richtlinien für den WIP. VPN-Empfehlungen zu best Practices finden Sie unter [VPNv2 CSP](vpnv2-csp.md).

Weitere Informationen zu WIP finden Sie in den folgenden TechNet-Themen:

-   [Erstellen Sie eine Richtlinie Windows Informationen Schutz (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/overview-create-wip-policy)
-   [Allgemeine Richtlinien und bewährte Methoden für den Windows-Schutz (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/guidance-and-best-practices-wip)

Das folgende Diagramm zeigt die EnterpriseDataProtection CSP im Strukturformat dar.

![Enterprisedataprotection Csp Diagramm](images/provisioning-csp-enterprisedataprotection.png)

<a href="" id="--device-vendor-msft-enterprisedataprotection"></a>**./Device/Vendor/MSFT/EnterpriseDataProtection**  
<p style="margin-left: 20px">Der Stammknoten für den CSP.

<a href="" id="settings"></a>**Einstellungen**  
<p style="margin-left: 20px">Der für die Konfigurationseinstellungen für den Windows Informationen Protection (WIP) Stammknoten.

<a href="" id="settings-edpenforcementlevel"></a>**Einstellungen/EDPEnforcementLevel**  
<p style="margin-left: 20px">Legen Sie die WIP Erzwingung der Ebene. Beachten Sie, dass diese Einstellung nicht ausreichend ist, WIP auf dem Gerät zu aktivieren. Versuche, diesen Wert ändern schlägt fehl, wenn die Bereinigung WIP ausgeführt wird.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) – deaktiviert / kein Schutz (entschlüsselt zuvor geschützte Daten).
-   1 – unbeaufsichtigten Modus (verschlüsseln und überwachen nur).
-   2 – Außerkraftsetzung Modus (verschlüsseln, auffordern und überwachen).
-   3 – Blockmodus (verschlüsseln, blockieren und überwachen).

<p style="margin-left: 20px">Unterstützte Vorgänge sind hinzufügen, Get, ersetzen und löschen. Werttyp ist Integer.

<a href="" id="settings-enterpriseprotecteddomainnames"></a>**Einstellungen/EnterpriseProtectedDomainNames**  
<p style="margin-left: 20px">Eine Liste der Domänen, die vom Unternehmen verwendet wird, für dessen Benutzeridentitäten getrennt durch Pipes ("|"). Die erste Domäne in der Liste muss die primäre Enterprise-ID, d. h., die ein, die die Verwaltung von Behörde für WIP sein. Benutzeridentitäten aus einem dieser Domänen gilt als ein Unternehmen verwaltetes Konto und zugeordnete Daten geschützt werden sollte. Beispielsweise würde die Domänen für alle e-Mail-Konten im Besitz des Unternehmens erwartet werden, in dieser Liste angezeigt werden. Versuche, diesen Wert ändern schlägt fehl, wenn die Bereinigung WIP ausgeführt wird.

<p style="margin-left: 20px">Ändern der primären Enterprise-ID wird nicht unterstützt und kann dazu führen, dass unerwartetes Verhalten auf dem Client.

> **Hinweis**  Der Client erfordert Domänennamen ein, um die kanonische werden, andernfalls wird die Einstellung vom Client zurückgewiesen.

 

<p style="margin-left: 20px">Hier sind die Schritte kanonische Domänennamen zu erstellen:

1.  Umwandeln Sie die ASCII-Zeichen (nur A – Z) in Kleinbuchstaben. Beispielsweise Microsoft.COM -&gt; microsoft.com.
2.  Rufen Sie [IdnToAscii](https://msdn.microsoft.com/library/windows/desktop/dd318149.aspx) mit IDN\_VERWENDUNG\_STD3\_ASCII\_REGELN wie die Kennzeichen.
3.  Anruf [IdnToUnicode](https://msdn.microsoft.com/library/windows/desktop/dd318151.aspx) ohne Kennzeichen Set (DwFlags = 0).

<p style="margin-left: 20px">Unterstützte Vorgänge sind hinzufügen, Get, ersetzen und löschen. Werttyp ist Zeichenfolge.

<a href="" id="settings-allowuserdecryption"></a>**Einstellungen/AllowUserDecryption**  
<p style="margin-left: 20px">Ermöglicht es dem Benutzer Dateien entschlüsseln. Wenn diese Eigenschaft auf 0 (nicht zulässig) gesetzt ist, wird der Benutzer nicht Schutz von Unternehmensinhalten über das Betriebssystem oder die Anwendung Benutzererlebnis entfernen sein.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – nicht zugelassen.
-   1 (Standard) – zulässig.

<p style="margin-left: 20px">Am stärksten eingeschränkten Wert ist 0.

<p style="margin-left: 20px">Unterstützte Vorgänge sind hinzufügen, Get, ersetzen und löschen. Werttyp ist Integer.

<a href="" id="settings-requireprotectionunderlockconfig"></a>**Einstellungen/RequireProtectionUnderLockConfig**  
<p style="margin-left: 20px">Gibt an, ob der Schutz unter Sperre Feature (auch bekannt als unter PIN-Nummer verschlüsseln) konfiguriert werden soll.

<p style="margin-left: 20px">Der Kryptografiedienstanbieter überprüft die aktuelle Edition und Hardware-Unterstützung (TPM) und gibt eine Fehlermeldung zurück, wenn das Gerät nicht über die erforderliche Hardware verfügt.

> **Hinweis**  Diese Einstellung wird nur in Windows 10 Mobile unterstützt.

 

<p style="margin-left: 20px">Unterstützte Vorgänge sind hinzufügen, Get, ersetzen und löschen. Werttyp ist Integer.

<a href="" id="settings-datarecoverycertificate"></a>**Einstellungen/DataRecoveryCertificate**  
<p style="margin-left: 20px">Gibt ein Recovery-Zertifikat, das für die Wiederherstellung von Daten verschlüsselter Dateien verwendet werden kann. Dies ist identisch mit den Daten Recovery-Agent (DRA) Zertifikat zum Verschlüsseln von Dateisystem (EFS), nur durch MDM anstelle von Gruppenrichtlinien bereitgestellt.

> **Hinweis**  Wenn diese Richtlinie und die entsprechende Einstellung Gruppenrichtlinien konfiguriert sind, wird die Einstellung der Gruppenrichtlinie erzwungen.

<p style="margin-left: 20px">DRA Informationen aus MDM Richtlinie muss serialisierten binäres Blob, was wir von GP erwarten identisch sein.
Das binäre Blob ist die serialisierte Version der folgenden Struktur:

``` syntax
//
//  Recovery Policy Data Structures
//
 
typedef struct _RECOVERY_POLICY_HEADER {
    USHORT      MajorRevision;
    USHORT      MinorRevision;
    ULONG       RecoveryKeyCount;
} RECOVERY_POLICY_HEADER, *PRECOVERY_POLICY_HEADER;
 
typedef struct _RECOVERY_POLICY_1_1    {
        RECOVERY_POLICY_HEADER  RecoveryPolicyHeader;
        RECOVERY_KEY_1_1        RecoveryKeyList[1];
}   RECOVERY_POLICY_1_1, *PRECOVERY_POLICY_1_1;
 
#define EFS_RECOVERY_POLICY_MAJOR_REVISION_1   (1)
#define EFS_RECOVERY_POLICY_MINOR_REVISION_0   (0)
 
#define EFS_RECOVERY_POLICY_MINOR_REVISION_1   (1)
 
///////////////////////////////////////////////////////////////////////////////
//                                                                            /
//  RECOVERY_KEY Data Structure                                               /
//                                                                            /
///////////////////////////////////////////////////////////////////////////////
 
//
// Current format of recovery data.
//
 
typedef struct _RECOVERY_KEY_1_1   {
        ULONG               TotalLength;
        EFS_PUBLIC_KEY_INFO PublicKeyInfo;
} RECOVERY_KEY_1_1, *PRECOVERY_KEY_1_1;
 
 
typedef struct _EFS_PUBLIC_KEY_INFO {
 
    //
    // The length of this entire structure, including string data
    // appended to the end. The length should be a multiple of 8 for
    // 64 bit alignment
    //
 
    ULONG Length;
 
    //
    // Sid of owner of the public key (regardless of format).
   // This field is to be treated as a hint only.
    //
 
    ULONG PossibleKeyOwner;
 
    //
    // Contains information describing how to interpret
    // the public key information
    //
 
    ULONG KeySourceTag;
 
    union {
 
        struct {
 
            //
            // The following fields contain offsets based at the
            // beginning of the structure.  Each offset is to
            // a NULL terminated WCHAR string.
            //
 
            ULONG ContainerName;
            ULONG ProviderName;
 
            //
            // The exported public key used to encrypt the FEK.
            // This field contains an offset from the beginning of the
            // structure.
            //
 
            ULONG PublicKeyBlob;
 
            //
            // Length of the PublicKeyBlob in bytes
            //
 
            ULONG PublicKeyBlobLength;
 
        } ContainerInfo;
 
        struct {
 
            ULONG CertificateLength;       // in bytes
            ULONG Certificate;             // offset from start of structure
 
        } CertificateInfo;
 
 
        struct {
 
            ULONG ThumbprintLength;        // in bytes
            ULONG CertHashData;            // offset from start of structure
 
        } CertificateThumbprint;
    };
 
 
 
} EFS_PUBLIC_KEY_INFO, *PEFS_PUBLIC_KEY_INFO;
 
//
// Possible KeyTag values
//
 
typedef enum _PUBLIC_KEY_SOURCE_TAG {
    EfsCryptoAPIContainer = 1,
    EfsCertificate,
    EfsCertificateThumbprint
} PUBLIC_KEY_SOURCE_TAG, *PPUBLIC_KEY_SOURCE_TAG;
 
```

<p style="margin-left: 20px">Für EFSCertificate KeyTag wird es erwartet, dass eine der-CODIERTES Binäres Zertifikat werden.

<p style="margin-left: 20px">Unterstützte Vorgänge sind hinzufügen, Get, ersetzen und löschen. Werttyp ist Base64-codierte Zertifikat.

<a href="" id="settings-revokeonunenroll"></a>**Einstellungen/RevokeOnUnenroll**  
<p style="margin-left: 20px">Diese Richtlinie steuert, ob die Schlüssel WIP widerrufen, wenn ein Gerät vom Verwaltungsdienst unenrolls. Wenn auf 0 (keine Schlüssel widerrufen) festlegen, die Schlüssel nicht aufgehoben werden, und der Benutzer weiterhin Zugriff auf geschützte Dateien nach Unenrollment haben. Wenn der Schlüssel nicht gesperrt sind, wird kein Cleanup gesperrte Datei anschließend. Vor dem Senden des Befehls Unenroll, wenn Sie möchten eine selektive Remotegerätzurücksetzung soll, wenn es unenrolled, ist ein Gerät sollten Sie explizit diese Richtlinie auf 1 festlegen.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 – widerrufen keine von Schlüsseln.
-   1 (Standard) – Revoke-Schlüssel.

<p style="margin-left: 20px">Unterstützte Vorgänge sind hinzufügen, Get, ersetzen und löschen. Werttyp ist Integer.

<a href="" id="settings-rmstemplateidforedp"></a>**Einstellungen/RMSTemplateIDForEDP**  
<p style="margin-left: 20px">TemplateID die GUID, für die RMS-Verschlüsselung verwenden. Die Vorlage RMS ermöglicht der IT-Administrator die Details zu konfigurieren, hat Zugriff auf RMS geschützte Datei und wie lange sie Zugriff haben.

<p style="margin-left: 20px">Unterstützte Vorgänge sind hinzufügen, Get, ersetzen und löschen. Werttyp ist String (GUID).

<a href="" id="settings-allowazurermsforedp"></a>**Einstellungen/AllowAzureRMSForEDP**  
<p style="margin-left: 20px">Gibt an, ob Azure RMS-Verschlüsselung für WIP zulassen.

-   0 (Standard) – verwenden nicht RMS.
-   1 – verwenden Sie RMS.

<p style="margin-left: 20px">Unterstützte Vorgänge sind Add, Get, ersetzen und löschen. Werttyp ist Integer.

<a href="" id="settings-edpshowicons"></a>**Einstellungen/EDPShowIcons**  
<p style="margin-left: 20px">Bestimmt, ob Überlagerungen hinzugefügt werden Symbole für WIP Dateien im Explorer und Enterprise nur app Kacheln im Startmenü geschützt.

<p style="margin-left: 20px">In der folgenden Liste sind die unterstützten Werte:

-   0 (Standard) - Nr. WIP überlagert auf Symbole oder Kacheln.
-   1 – zeigen Sie WIP überlagert auf geschützte Dateien und apps, die nur Unternehmensinhalten erstellen können an.

<p style="margin-left: 20px">Unterstützte Vorgänge sind hinzufügen, Get, ersetzen und löschen. Werttyp ist Integer.

<a href="" id="status"></a>**Status**  
<p style="margin-left: 20px">Eine nur-Lese-Bitmaske, die den aktuellen Status des WIP auf dem Gerät angibt. Der Dienst MDM kann diesen Wert verwenden, um den aktuellen Status WIP insgesamt zu bestimmen. WIP ist nur auf (0 = 1 Bit), wenn WIP obligatorisch Policies and Settings ab WIP AppLocker konfiguriert sind.

<p style="margin-left: 20px">Vorgeschlagene Werte:

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Für künftige Zwecke vorbehalten</p></td>
<td><p>Obligatorische WIP-Einstellungen</p>
<p>Legen Sie = 1</p>
<p>Nicht festlegen = 0</p></td>
<td><p>Für künftige Zwecke vorbehalten</p></td>
<td><p>AppLocker konfiguriert</p>
<p>Ja = 1</p>
<p>Nein = 0</p></td>
<td><p>WIP = 1</p>
<p>WIP aus = 0</p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p>3</p></td>
<td><p>2</p></td>
<td><p>1</p></td>
<td><p>0</p></td>
</tr>
</tbody>
</table>

 

<p style="margin-left: 20px">Bit 0 gibt an, ob WIP aktiviert oder deaktiviert ist.

<p style="margin-left: 20px">Bit 1 gibt an, ob AppLocker WIP Richtlinien festgelegt werden.

<p style="margin-left: 20px">Bit 3 gibt an, ob die obligatorischen WIP Richtlinien konfiguriert sind. Wenn eine oder mehrere der obligatorischen WIP Richtlinien nicht konfiguriert sind, wird das Bit 3 auf 0 (null) festgelegt.

<p style="margin-left: 20px">Hier wird die Liste der obligatorisch WIP Richtlinien:

-   EDPEnforcementLevel im Bereich CSP EnterpriseDataProtection
-   DataRecoveryCertificate im Bereich CSP EnterpriseDataProtection
-   EnterpriseProtectedDomainNames im Bereich CSP EnterpriseDataProtection
-   NetworkIsolation/EnterpriseIPRange in Gruppenrichtlinien CSP
-   NetworkIsolation/EnterpriseNetworkDomainNames in CSP-Richtlinie

<p style="margin-left: 20px">BITS 2 und 4 sind für die zukünftige Verwendung reserviert.

<p style="margin-left: 20px">Unterstützte Vorgang ist Get. Werttyp ist Integer.

 

 





