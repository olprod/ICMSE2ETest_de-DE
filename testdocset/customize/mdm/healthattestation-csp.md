---
title: HealthAttestation CSP
description: HealthAttestation CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 6F2D783C-F6B4-4A81-B9A2-522C4661D1AC
ms.openlocfilehash: a5a096cc0247a97f31361dd24edd6e153481eb29
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="healthattestation-csp"></a>HealthAttestation CSP


Der Dienstanbieter für HealthAttestation Konfiguration ermöglicht Enterprise IT-Managern bewerten die Integrität der verwalteten Geräte und Aktionen Enterprise Richtlinie.

Es folgt eine Liste der Funktionen, die vom HealthAttestation CSP ausgeführt:

-   Erfasst Daten, die bei der Überprüfung einer Zustände Geräte verwendet wird
-   Die Daten weitergeleitet des Health Bescheinigung Service (HAS).
-   Stellt das Health Bescheinigung Zertifikat, das sie von HAS erhält bereit
-   Auf Anfrage, leitet das Health Bescheinigung Zertifikat (Empfangen von HAS) und verwandte zur Laufzeit an den MDM Server für die Überprüfung

Das folgende Diagramm zeigt den HealthAttestation Konfiguration-Dienstanbieter in der Strukturformat.

![Healthattestation csp](images/provisioning-csp-healthattestation.png)

<a href="" id="--vendor-msft"></a>**./Vendor/MSFT**  
Der Stammknoten für den HealthAttestation Konfigurationsdienstanbieter.

<a href="" id="verifyhealth--required-"></a>**VerifyHealth** (Erforderlich)  
So bereiten Sie eine Anforderung Health Überprüfung vor das Gerät benachrichtigt.

Der unterstützte Vorgang ist ausführen.

<a href="" id="status--required-"></a>**Status** (Erforderlich)  
Den aktuellen Status der Anforderung Health enthält.

Der unterstützte Vorgang ist Get.

In der folgenden Liste sind die unterstützten Werte:

-   1 – HEALTHATTESTATION\_CERT\_RETRI\_nicht INITIALISIERT Vorbereiten einer Anforderung ein neues Integritätszertifikat des Health Bescheinigung Service (HAS) abgerufen.
-   2 – HEALTHATTESTATION\_CERT\_RETRI\_ANGEFORDERT wartet für Health-Bescheinigung (HAS) um wieder zu reagieren.
-   3 – HEALTHATTESTATION\_CERT\_RETRI\_VOLLSTÄNDIGE Gesundheitsdaten ist für die Entnahme von bereit.

<a href="" id="forceretrieve--optional-"></a>**ForceRetrieve** (Optional)  
Weist den Client zum Initiieren einer neuen Anforderung Health Zertifikat aus Health Bescheinigung Service (HAS) und Abrufen eines neuen Zertifikats Integrität. Diese Option sollte verwendet werden, wenn der MDM Server eine Zertifikat Aktualität Richtlinie erzwingt. Darüber hinaus benötigen Sie ein Zertifikat, das in der Überprüfung Anforderungszeit erstellt wird.

Der unterstützte Vorgang ist ersetzen.

<a href="" id="certificate--required-"></a>**Zertifikat** (Erforderlich)  
Weist Health Zertifikat Gesundheitsdaten, die mit der Nonce gepackt ist und verwandte Gesundheitsdaten (aktuelle PCR Werte) weiterleiten an den MDM Server in einem verschlüsselten Format.

Der unterstützte Vorgang ist Get.

<a href="" id="nonce--required-"></a>**Nonce** (Erforderlich)  
Schützt die Integrität Bescheinigung Kommunikation mit einer kryptografischen Nonce, die vom Server MDM generiert wird.

Die Nonce ist im hex-Format mit einer Mindestgröße von 8 Bytes und eine maximale Größe von 32 Bytes.

Der unterstützte Vorgang ist ersetzen.

<a href="" id="correlationid--required-"></a>**CorrelationId** (Erforderlich)  
CorrelationID ist einen decimal-Wert, der einen Anruf für ein Zertifikat Health identifiziert. Kann zum Korrelieren Health Bescheinigung Server (HAS) Protokolle mit den MDM Ereignis Server und Client-Ereignisprotokollen zum Debuggen, Audit oder zur Problembehandlung verwendet werden.

Der unterstützte Vorgang ist Get.

## <a name="integrating-health-attestation"></a>**Integrieren von Bescheinigung**


Um Bescheinigung in Ihrer Umgebung zu integrieren, müssen Sie die folgenden Schritte ausführen:

1.  [Überprüfen Sie den HTTPS-Zugriff](#verify-access)
2.  [Weisen Sie Client zur Vorbereitung der Überprüfung Gesundheitsdaten](#prepare-health-data)
3.  [Ausführen einer Aktion basierend auf der Antwort des clients](#take-action-client-response)
4.  [Weisen Sie den Client Bescheinigung Gesundheitsdaten zur Überprüfung weiterleiten](#forward-health-attestation)
5.  [Weiterleiten Sie Bescheinigung Gesundheitsdaten, Health Bescheinigung Service (HAS)](#foward-data-to-has)
6.  [Antwort von HAS erhalten](#receive-has-response)
7.  [Ausführen einer entsprechende Richtlinienaktion basierend auf der Ergebnisse der Auswertung](#take-policy-action)

Jeder Schritt wird in den folgenden Abschnitten dieses Themas ausführlich beschrieben.

## <a name="a-href-idverify-accessaverify-https-access"></a><a href="" id="verify-access"></a>**Überprüfen des Zugriffs auf HTTPS**


Überprüfen Sie, ob die MDM Server und das Gerät (Client MDM) **has.spserv.microsoft.com** über das TCP-Protokoll über Port 443 (HTTPS) zugreifen können.

## <a name="a-href-idprepare-health-dataainstruct-client-to-prepare-health-data-for-verification"></a><a href="" id="prepare-health-data"></a>**Weisen Sie Client zur Vorbereitung der Überprüfung Gesundheitsdaten**


Nachdem Access überprüft worden ist, registrieren Sie einen unteilbare SyncML-Anruf an die Statusdaten-Auflistung zu starten.

Das folgende Beispiel zeigt einen Beispiel unteilbare Aufruf, der Auflistung und die Überprüfung der Integrität Bescheinigung Daten aus einem verwalteten Gerät ausgelöst wird.

``` syntax
<SyncML xmlns="SYNCML: SYNCML1.2">

    // Header starts here 
    <SyncHdr>
        <VerDTD> 1.2 </VerDTD>
        <VerProto> DM/1.2 </VerProto>
        <SessionID> [Session ID] </SessionID>
        <MsgID> [Message ID] </MsgID>
        <Target>
            <LocURI> ./Vendor/MSFT/HealthAttestation/Certificate 
        </LocURI>
        </Target>
        <Source>
            <LocURI> [URL of MDM Server] </LocURI>
        </Source>
    </SyncHdr>

    // Body starts here 
    <SyncBody>
    
    //Start an atomic call
        <Atomic>
            <CmdID> [Command ID] </CmdID>

            //The first item is an optional call.
            //"ForceRetrieve" node instructs the client to
            //initiate a new request to Health certificate from 
            //Health Attestation Service (HAS), get a new health
            //certificate. This option should be used if MDM 
            //server enforces a certificate freshness policy, 
            //requires a certificate that is created at 
            //verification request time.  
            <Set>
                <CmdID> [Command ID] </CmdID>
                <Item>
                    <Target>
                      <LocURI>
                  ./Vendor/MSFT/HealthAttestation/ForceRetrieve
                      </LocURI>
                    </Target>
                </Item>
            </Set>

            //Tell the device to create an encrypted payload that
            //contains health attestation related data  
            <Exec>
                <CmdID> [Command ID] </CmdID>
                <Item>
                    <Target>
                      <LocURI> 
                ./Vendor/MSFT/HealthAttestation/VerifyHealth
       </LocURI>
                    </Target>
                </Item>
            </Exec>

            //Forward a cryptographic strong nonce to the client
            //The nonce must be a hexadecimal string that is
            //between 8 and 32 bytes
            <Set>
                <CmdID> [Command ID] </CmdID>
                <Item>
                    <Target>
                      <LocURI> ./Vendor/MSFT/HealthAttestation/Nonce
                      </LocURI>
                    </Target>
                    <Data> [hexadecimal string] </Data>
                </Item>
            </Set>

            //Ask for status
            <Get>
                <CmdID> [Command ID] </CmdID>
                <Item>    
                    <Target>
                      <LocURI> 
              ./Vendor/MSFT/HealthAttestation/Status
                      </LocURI>
                    </Target>
                </Item>
            </Get>
        </Atomic>
    </SyncBody>   
</SyncML>
```

## <a name="a-href-idtake-action-client-responseatake-action-based-on-the-clients-response"></a><a href="" id="take-action-client-response"></a>**Ausführen einer Aktion basierend auf der Antwort des clients**


Nachdem der Client die Integrität Bescheinigung Anforderung empfängt, sendet er eine Antwort. Die folgende Liste beschreibt die Antworten zusammen mit einer empfohlenen auszuführende Aktion:

-   Ist die Antwort auf einen der Knoten, die aufgerufen werden "Failed" entsprechenden Maßnahmen ergreifen, und klicken Sie dann die Anforderung erneut übermitteln.
-   Wenn die Antwort **HEALTHATTESTATION\_CERT\_RETRI\_ANGEFORDERT (1)** oder **HEALTHATTESTATION\_CERT\_RETRI\_nicht INITIALISIERT (0)** warten, bis eine Warnung (ein Client initiierte Anforderung, die dem MDM Server weist die Statusdaten gepackt und bereit zur Entnahme von ist, werden mit dem nächsten Abschnitt fortfahren.)
-   Wenn die Antwort **HEALTHATTESTATION\_CERT\_RETRI\_COMPLETE(3)** fahren Sie dann mit dem nächsten Abschnitt fort.

## <a name="a-href-idforward-health-attestationainstruct-the-client-to-forward-health-attestation-data-for-verification"></a><a href="" id="forward-health-attestation"></a>**Weisen Sie den Client Bescheinigung Gesundheitsdaten zur Überprüfung weiterleiten**


Im nächsten Schritt müssen die Bescheinigung Gesundheitsdaten, damit die Daten überprüft werden können weitergeleitet. Erstellen einen unteilbare Aufruf an den Knoten Zertifikat und CallIdentifier und dazu, nehmen Sie eine verschlüsselte Nutzlast an, die ein Health Zertifikat und zugehörigen Daten vom Gerät umfasst.

Das folgende Beispiel zeigt einen Beispiel unteilbare Anruf:

``` syntax
<SyncML xmlns="SYNCML: SYNCML1.2">

    // Header Starts here 
    <SyncHdr>
        <VerDTD> 1.2 </VerDTD>
        <VerProto> DM/1.2 </VerProto>
        <SessionID> [Session ID] </SessionID>
        <MsgID> [Message ID] </MsgID>
        <Target>
            <LocURI>./Vendor/MSFT/HealthAttestation/Certificate
            </LocURI>
        </Target>
        <Source>
            <LocURI> [URL of MDM Server] </LocURI>
        </Source>
    </SyncHdr>

    // Body Starts here 
    <SyncBody>
    
    //Start an atomic call
        <Atomic>

            //Call Health CSP to get the packaged data and 
            //call identifier 
            <CmdID> [Command ID] </CmdID>

            //Get the packaged data
            <Get>
                <CmdID> [Command ID] </CmdID>
                <Item>    
                    <Target>
                   <LocURI>
                    ./Vendor/MSFT/HealthAttestation/Certificate
                    </LocURI>
                    </Target>
                </Item>
            </Get>
    
            //Get the health attestation call identifier 
            <Get>
                <CmdID> [Command ID] </CmdID>
                <Item>    
                    <Target>
                      <LocURI>
                      ./Vendor/MSFT/HealthAttestation/CorrelationId
                      </LocURI>
                    </Target>
                </Item>
            </Get>
        </Atomic>
    </SyncBody>   

</SyncML>
```

## <a name="a-href-idfoward-data-to-hasaforward-health-attestation-data-to-health-attestation-service-has"></a><a href="" id="foward-data-to-has"></a>**Weiterleiten von Bescheinigung Gesundheitsdaten zu Integrität Bescheinigung Service (HAS)**


Als Antwort auf die Anforderung, die im vorherigen Schritt gesendet wurde, leitet der Client MDM ein Blob XML-Format und eine Anruf-ID im folgenden Format weiter.

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<HealthCertificateValidationRequest ProtocolVersion="1" 
    xmlns="http://schemas.microsoft.com/windows/security/healthcertificate/validation/request/v1">
    <Claims> [base64 blob, eg ‘ABc123+/…==’] </Claims>
    <HealthCertificateBlob> [base64 blob, eg ‘ABc123+/...==’]
    </HealthCertificateBlob>
</HealthCertificateValidationRequest>
```

Wenn der MDM Server die oben angegebenen Daten erhält, müssen sie den Anrufbezeichner (für Referenzzwecke) zum Anruf korreliert anmelden. Hinzufügen der Nonce, die in der XML-Blob generiert wurde, die sie von der Client - erhalten hat, und klicken Sie dann die Daten im folgenden Format zu Integrität Bescheinigung Service (HAS) weiterleiten (HTTP Post)

``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs=http://www.w3.org/2001/XMLSchema
xmlns=http://schemas.microsoft.com/windows/security/healthcertificate/validation/request/v1  targetNamespace=http://schemas.microsoft.com/windows/security/healthcertificate/validation/request/v1  elementFormDefault="qualified">
<xs:element name="HealthCertificateValidationRequest" type="HealthCertificateValidationRequest_T"/>
  <xs:complexType name="HealthCertificateValidationRequest_T">
    <xs:annotation>
      <xs:documentation> A request for Health Certificate 
   validation </xs:documentation>
    </xs:annotation>
    <xs:sequence>
      <xs:element name="Nonce" type="xs:hexBinary"/>
      <xs:element name="Claims" type="xs:base64Binary"/>
      <xs:element name="HealthCertificateBlob" 
    type="xs:base64Binary"/>
    </xs:sequence>
    <xs:attribute name="ProtocolVersion" use="required">
      <xs:simpleType>
        <xs:restriction base="xs:int">
          <xs:minInclusive value="1"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:attribute>
  </xs:complexType>
</xs:schema>
```

## <a name="a-href-idreceive-has-responseareceive-response-from-the-has"></a><a href="" id="receive-has-response"></a>**Antwort von der HAS erhalten**


Wenn die Bescheinigung Health Service eine Anforderung zur Überprüfung empfängt, führt er die folgenden Schritte aus:

-   Entschlüsselt die verschlüsselten Daten, die er erhält.
-   Überprüft die Statusdaten.
-   Überprüft, ob nicht ist, die eine Anforderung wiederholen Überprüfung der Nonce, die in verschlüsselten Blob, gegen die Nonce eingebettet ist, die er vom Server MDM erhält.
-   Erstellt einen Bericht im XML-Format und die Ergebnisse der Auswertung auf den MDM Server im folgenden Format weiterleitet.

    ``` syntax
    <?xml version=\"1.0\"?>

    <HealthCertificateValidationResponse 
       xmlns:xsd=\"http://www.w3.org/2001/XMLSchema\" 
       xmlns:xsi=\"http://www.w3.org/2001/XMLSchema-instance\" 
       ErrorCode=\"0\" 
       xmlns=\"http://schemas.microsoft.com/windows/security/healthcertificate/validation/response/v1\">
        <HealthCertificateProperties>

            <Issued> 
                2015-02-23T17:43:27.5229876Z 
            </Issued>

            <AIKPresent>
                False
            </AIKPresent>

            <ResetCount>
                [INT]
            </ResetCount>

            <RestartCount> 
                [INT]
            </RestartCount>

            <DEPPolicy>
                [Boolean - 0, 1]
            </DEPPolicy>

            <BitlockerStatus> 
                [Boolean - 0, 1] 
            </BitlockerStatus>

            <BootManagerRevListVersion>
                [INT]
            </BootManagerRevListVersion>

            <CodeIntegrityRevListVersion>
                [INT] 
            </CodeIntegrityRevListVersion>

            <SecureBootEnabled> 
                [Boolean- 0, 1]
            </SecureBootEnabled>

            <BootDebuggingEnabled>
                [Boolean- 0, 1]
         </BootDebuggingEnabled>

            <OSKernelDebuggingEnabled>
                [Boolean-0, 1]
            </OSKernelDebuggingEnabled>
            
            <CodeIntegrityEnabled> 
                [Boolean - 0, 1]
            </CodeIntegrityEnabled>
            
            <TestSigningEnabled> 
                [Boolean - 0, 1]
            </TestSigningEnabled>
            
            <SafeMode> 
                [Boolean - 0, 1] 
            </SafeMode>
            
            <WinPE> 
                [Boolean - 0, 1] 
            </WinPE>
            
            <ELAMDriverLoaded> 
                [Boolean - 0, 1] 
            </ELAMDriverLoaded>
            
            <VSMEnabled> 
                [Boolean - 0, 1] 
            </VSMEnabled>
             
            <CIPolicyHash> 
                [INT] 
            </CIPolicyHash>

            <SBCPPolicyHash> 
                [INT] 
            </SBCPPolicyHash>

            <PCR0> 
                [INT] 
            </PCR0>
        
        </HealthCertificateProperties>

    </HealthCertificateValidationResponse>
    ```

## <a name="a-href-idtake-policy-actionatake-appropriate-policy-action-based-on-evaluation-results"></a><a href="" id="take-policy-action"></a>**Ausführen einer entsprechende Richtlinienaktion basierend auf der Ergebnisse der Auswertung**


Nachdem der MDM Server die überprüften Daten empfangen hat, kann die Informationen Richtlinie Entscheidungen treffen, bewerten Sie die Daten verwendet werden. Beispiele für möglichen Aktionen wäre:

-   Ermöglichen Sie den Gerätezugriff.
-   Zulassen Sie das Gerät auf die Ressourcen zugreifen, aber das Gerät zur weiteren Untersuchung kennzeichnen.
-   Verhindern Sie, dass ein Gerät auf Ressourcen zugreifen.

Es folgt eine Liste der Datenpunkte von des HAS bestätigt wurden:

-   AIKPresent
-   DEPPolicy
-   BitlockerStatus
-   SecureBootEnabled
-   CodeIntegrityEnabled
-   Abgesicherten Modus
-   Windows PE
-   ELAMDriverLoaded
-   VSMEnabled
-   BootDebuggingEnabled
-   OSKernelDebuggingEnabled
-   TestSigningEnabled
-   BootManagerRevListVersion
-   CodeIntegrityRevListVersion
-   CIPolicyHash
-   SBCPPolicyHash
-   PCR0

Jede dieser werden ausführlicher in den folgenden Abschnitten zusammen mit den empfohlenen Maßnahmen für die Erhaltung beschrieben.

<a href="" id="aikpresent"></a>**AIKPresent**  
Wenn eine Bescheinigung Identität Schlüssel (AIK) auf einem Gerät vorhanden ist, bedeutet dies, dass das Gerät ein Vermerk Schlüssel (EK) Zertifikat verfügt. Mehr als ein Gerät vertrauenswürdigen möglich, die ein Zertifikat EK besitzt.

Wenn AIKPresent = 1 (True), und klicken Sie dann zulassen.

Wenn AIKPresent = False (0), und führen Sie eine der folgenden Aktionen, die mit Ihrer Unternehmensrichtlinien ausrichten:

-   Nicht alle Access zulassen
-   Sperren des Zugriffs auf HBI-Ressourcen
-   Zugriff für bedingte basierend auf anderen von Datenpunkten, die zur Evaluierung Zeit vorhanden sind. Beispielsweise andere Attribute auf Zertifikat oder ein Geräten ältere Vertrauensstellung Verlauf und Aktivitäten.
-   Führen Sie eine der vorherigen Aktionen, und platzieren Sie das Gerät darüber in eine Überwachungsliste das Gerät zum potenziellen Risiken besser überwachen.

<a href="" id="deppolicy"></a>**DEPPolicy**  
Ein Gerät kann mehr vertrauenswürdig sein, wenn die DEP-Richtlinie auf dem Gerät aktiviert ist.

Richtlinien für die Datenausführungsverhinderung (DEP) für Daten definiert ist ein Satz von Hardware und Software-Technologien, die zusätzliche überprüft auf Arbeitsspeicher, um zu verhindern, dass bösartigen Code auf einem System ausgeführt werden soll. Sichere Boot ermöglicht eine eingeschränkte Liste auf X86/amd64 und auf ARM NTOS sperrt er auf on.

DEPPolicy kann deaktiviert oder mithilfe der folgenden Befehle in WMI oder ein PowerShell-Skript aktiviert werden:

-   Um die Datenausführungsverhinderung deaktivieren möchten, geben Sie **bcdedit.exe / {aktuelle} Set n x AlwaysOff**
-   Zum Aktivieren der Datenausführungsverhinderung Geben Sie **bcdedit.exe/Set {aktuelle} n x AlwaysOn**

Wenn DEPPolicy = 1 (aktiviert), und klicken Sie dann zulassen.

Wenn DEPPolicy = 0 (Off), und führen Sie eine der folgenden Aktionen, die mit Ihrer Unternehmensrichtlinien ausrichten:

-   Nicht alle Access zulassen
-   Sperren des Zugriffs auf HBI-Ressourcen
-   Zugriff für bedingte basierend auf anderen von Datenpunkten, die zur Evaluierung Zeit vorhanden sind. Beispielsweise andere Attribute auf Zertifikat oder ein Geräten ältere Vertrauensstellung Verlauf und Aktivitäten.
-   Führen Sie eine der vorherigen Aktionen, und platzieren Sie das Gerät darüber in eine Überwachungsliste das Gerät zum potenziellen Risiken besser überwachen.

<a href="" id="bitlockerstatus"></a>**BitlockerStatus**  
Wenn Bitlocker aktiviert ist, kann das Gerät Daten zu schützen, die auf dem Laufwerk vor nicht autorisiertem Zugriff gespeichert wird, wenn das System ausgeschaltet ist oder zu dem Ruhezustand wechselt.

Windows BitLocker Drive Encryption verschlüsselt alle Daten, die auf dem Windows-Betriebssystem Datenträger gespeichert. BitLocker verwendet das TPM zum Schutz der Windows-Betriebssystem und Benutzerdaten und wird sichergestellt, dass ein Computer nicht manipuliert wurde, auch wenn es unbeaufsichtigte, verlorenen oder gestohlenen bleibt.

Wenn der Computer mit einem kompatiblen TPM ausgestattet ist, verwendet BitLocker das TPM zum Sperren der Verschlüsselungsschlüssel, die die Daten zu schützen. Dementsprechend werden die Schlüssel können nicht zugegriffen werden, bis das TPM den Zustand des Computers überprüft hat.

Wenn BitLockerStatus = 1 (aktiviert), und klicken Sie dann zulassen.

Wenn BitLockerStatus = 0 (Off), und führen Sie eine der folgenden Aktionen, die mit Ihrer Unternehmensrichtlinien ausrichten:

-   Nicht alle Access zulassen
-   Sperren des Zugriffs auf HBI-Ressourcen
-   Zugriff für bedingte basierend auf anderen von Datenpunkten, die zur Evaluierung Zeit vorhanden sind. Beispielsweise andere Attribute auf Zertifikat oder ein Geräten ältere Vertrauensstellung Verlauf und Aktivitäten.
-   Führen Sie eine der vorherigen Aktionen, und platzieren Sie das Gerät darüber in eine Überwachungsliste das Gerät zum potenziellen Risiken besser überwachen.

<a href="" id="securebootenabled"></a>**SecureBootEnabled**  
Wenn Secure Boot aktiviert ist, wird das System erzwungen, einen vertrauenswürdigen Factory Zustand zu starten. Wenn Secure Boot aktiviert ist, müssen die Hauptkomponenten zum Starten des Computers verwendet richtige kryptografische Signaturen werden, die von der Organisation als vertrauenswürdig gelten, die das Gerät hergestellt. UEFI-Firmware wird dadurch überprüft, bevor sie den Computer starten können. Wenn keine Dateien manipuliert wurden, startet Knacken ihre Signatur das System nicht.

Wenn SecureBootEnabled = 1 (True), und klicken Sie dann Zugriff gewähren.

Wenn SecurebootEnabled = 0 (False), und führen Sie eine der folgenden Aktionen, die mit Ihrer Unternehmensrichtlinien ausrichten:

-   Nicht alle Access zulassen
-   Sperren des Zugriffs auf HBI-Ressourcen
-   Zugriff für bedingte basierend auf anderen von Datenpunkten, die zur Evaluierung Zeit vorhanden sind. Beispielsweise andere Attribute auf Zertifikat oder ein Geräten ältere Vertrauensstellung Verlauf und Aktivitäten.
-   Führen Sie eine der vorherigen Aktionen, und platzieren Sie das Gerät darüber in eine Überwachungsliste das Gerät zum potenziellen Risiken besser überwachen.

<a href="" id="codeintegrityenabled"></a>**CodeIntegrityEnabled**  
Ausführen des Codes ist auf Integrität beschränkt, wenn die Integrität des Codes aktiviert ist, Code überprüft.

Integrität des Codes ist ein Feature, das die Integrität einer Datei Treiber oder System jedes Mal prüft, wenn es in den Arbeitsspeicher geladen wird. Integrität des Codes ermittelt, ob eine nicht signierte Treiber oder System-Datei in den Kernel geladen wird, oder eine Systemdatei von Schadsoftware geändert wurde, die von einem Benutzerkonto mit Administratorrechten ausgeführt wird.

Kernelmodus-Treiber müssen auf X64-basierten Versionen des Betriebssystems digital signiert werden.

Wenn CodeIntegrityEnabled = 1 (True), und klicken Sie dann Zugriff gewähren.

Wenn CodeIntegrityEnabled = 0 (False) und dann führen Sie eine der folgenden Aktionen, die mit Ihrer Unternehmensrichtlinien ausrichten:

-   Nicht alle Access zulassen
-   Sperren des Zugriffs auf HBI-Ressourcen
-   Zugriff für bedingte basierend auf anderen von Datenpunkten, die zur Evaluierung Zeit vorhanden sind. Beispielsweise andere Attribute auf die Integritätszertifikat oder ein Geräten erledigte Aktivitäten und Vertrauensstellung Verlauf.
-   Führen Sie eine der vorherigen Aktionen, und platzieren Sie das Gerät darüber in eine Überwachungsliste das Gerät zum potenziellen Risiken besser überwachen.

<a href="" id="safemode"></a>**Abgesicherten Modus**  
Abgesicherter Modus ist eine Option zur Problembehandlung für Windows, Ihrem Computer in einem eingeschränkten Status gestartet wird. Nur die grundlegenden Dateien und Treiber erforderliche zum Ausführen von Windows gestartet wurden.

Wenn abgesicherten Modus = 0 (False), und klicken Sie dann Zugriff gewähren.

Wenn abgesicherten Modus = 1 (True), und führen Sie eine der folgenden Aktionen, die mit Ihrer Unternehmensrichtlinien ausrichten:

-   Nicht alle Access zulassen
-   Sperren des Zugriffs auf HBI-Ressourcen
-   Auslösen einer Maßnahme, wie informiert das Team technischen Support zu wenden Sie sich an den Besitzer das Problem untersuchen.

<a href="" id="winpe"></a>**Windows PE**  
Vor der Installation einer Windows-Umgebung (Windows PE) ist ein minimales Betriebssystem mit eingeschränkten Diensten zum Vorbereiten eines Computers für die Installation von Windows, zum Kopieren von Datenträgerabbildern von einem Netzwerk-Dateiserver und zum Initiieren von Windows Setup verwendet wird.

Wenn Windows PE = 0 (False), und klicken Sie dann zulassen.

Wenn Windows PE = 1 (True), und klicken Sie dann Einschränken des Zugriffs auf remote-Ressourcen, die für die Installation von Windows-Betriebssystem erforderlich sind.

<a href="" id="elamdriverloaded"></a>**ELAMDriverLoaded**  
Frühe Einführung Anti-Malware (ELAM) bietet Schutz für die Computer in Ihrem Netzwerk beim start und vor dem Initialisieren von Drittanbieter-Treiber.

Wenn ELAMDriverLoaded = 1 (True), und klicken Sie dann Zugriff gewähren.

Wenn ELAMDriverLoaded = 0 (False) und dann eine der folgenden Aktionen, die Ihre Unternehmensrichtlinien für gibt an, ob es sich um ein desktop oder mobilen Gerät ist auch accounting ausgerichtet werden:

-   Nicht alle Access zulassen
-   Sperren des Zugriffs auf HBI-Ressourcen
-   Auslösen einer Maßnahme, wie informiert das Team technischen Support zu wenden Sie sich an den Besitzer das Problem untersuchen.

<a href="" id="vsmenabled"></a>**VSMEnabled**  
Virtuelle Secure Modus (VSM) ist ein Container, der hochwertige Ressourcen von einem betroffenen Kernel schützt. VSM erfordert ungefähr 1GB Arbeitsspeicher – es wurde soeben genügend Funktion LSA-Dienst auszuführen, der für alle Weitergabe-Authentifizierung verwendet wird.

VSM kann mithilfe des folgenden Befehls in WMI oder ein PowerShell-Skript aktiviert werden:

**Bcdedit.exe/Set {Current} Vsmlaunchtype auto**

Wenn ELAMDriverLoaded = 1 (True), und klicken Sie dann Zugriff gewähren.

Wenn ELAMDriverLoaded = 0 (False), und führen Sie eine der folgenden Aktionen, die mit Ihrer Unternehmensrichtlinien ausrichten:

-   Nicht alle Access zulassen
-   Sperren des Zugriffs auf HBI-Ressourcen
-   Auslösen einer Maßnahme, wie informiert das Team technischen Support zu wenden Sie sich an den Besitzer das Problem untersuchen.

**BootDebuggingEnabled** Debuggen starten aktiviert verweist auf ein Gerät, das in die Entwicklung und Tests verwendet wird. Geräte, die für die Entwicklung und Test, in der Regel verwendet werden sicherer sind: das Gerät möglicherweise instabil Code ausgeführt oder konfiguriert werden, mit weniger sicherheitseinschränkungen, die zum Testen und Entwicklung erforderlich ist.

Debuggen starten kann deaktiviert oder mithilfe der folgenden Befehle in WMI oder ein PowerShell-Skript aktiviert werden:

-   Geben Sie zum Deaktivieren von Debuggen Boot **bcdedit.exe/Set {aktuelle} Bootdebug deaktiviert**
-   Geben Sie zum Aktivieren von Debuggen Boot **bcdedit.exe/Set {aktuellen} Bootdebug auf**

Wenn BootdebuggingEnabled = 0 (False), und klicken Sie dann zulassen.

Wenn BootDebuggingEnabled = 1 (True), und führen Sie eine der folgenden Aktionen, die mit Ihrer Unternehmensrichtlinien ausrichten:

-   Nicht alle Access zulassen
-   Sperren des Zugriffs auf HBI-Ressourcen
-   Legen Sie das Gerät in einer Überwachungsliste das Gerät zum potenziellen Risiken besser überwachen.
-   Auslösen einer Maßnahme, beispielsweise aktivieren VSM mithilfe von WMI-Filterung oder ein Powershell-Skript.

**OSKernelDebuggingEnabled** OSKernelDebuggingEnabled verweist auf ein Gerät, das in die Entwicklung und Tests verwendet wird. Geräte, die für die Entwicklung und Test, in der Regel verwendet werden sicherer sind: sie möglicherweise instabil Code ausgeführt oder mit weniger sicherheitseinschränkungen für Tests und Entwicklung erforderlich konfiguriert werden.

Wenn OSKernelDebuggingEnabled = 0 (False), und klicken Sie dann Zugriff gewähren.

Wenn OSKernelDebuggingEnabled = 1 (True) ein, und führen Sie eine der folgenden Aktionen, die mit Ihrer Unternehmensrichtlinien ausrichten:

-   Nicht alle Access zulassen
-   Sperren des Zugriffs auf HBI-Ressourcen
-   Legen Sie das Gerät in einer Überwachungsliste das Gerät zum potenziellen Risiken besser überwachen.
-   Auslösen einer Maßnahme, wie beispielsweise darüber informiert, wenden Sie sich an den Besitzer des Supportteams das Problem zu untersuchen.

**TestSigningEnabled** Test Anmelden aktiviert ist, das Gerät erzwingt keine Überprüfung der Signatur während des Startvorgangs, und ermöglicht die nicht signierten Treiber (beispielsweise nicht signierte UEFI Module) beim Start geladen werden.

Test anmelden kann deaktiviert oder mithilfe der folgenden Befehle in WMI oder ein PowerShell-Skript aktiviert werden:

-   Geben Sie zum Deaktivieren von Debuggen Boot **bcdedit.exe {aktuelle} / Set Testsigning deaktiviert**
-   Geben Sie zum Aktivieren von Debuggen Boot **bcdedit.exe/Set {aktuelle} Testsigning auf**

Wenn TestSigningEnabled = 0 (False), und klicken Sie dann zulassen.

Wenn TestSigningEnabled = 1 (True) ein, und führen Sie eine der folgenden Aktionen, die mit Ihrer Unternehmensrichtlinien ausrichten:

-   Nicht alle Access zulassen
-   Sperren des Zugriffs auf HBI und MBI-Ressourcen
-   Legen Sie das Gerät in einer Überwachungsliste das Gerät zum potenziellen Risiken besser überwachen.
-   Auslösen einer Maßnahme, z. B. das Aktivieren der Test Signieren mit WMI-Filterung oder ein Powershell-Skript.

**BootManagerRevListVersion** Dieses Attribut gibt die Version der Start-Manager, die auf dem Gerät, um Ihnen ermöglichen, nachverfolgen und Verwalten der Sicherheits der Boot-Sequenz/Umgebung ausgeführt wird.

Wenn BootManagerRevListVersion = \[CurrentVersion\], klicken Sie dann auf Zugriff gewähren.

Wenn BootManagerRevListVersion! = \[CurrentVersion\], führen Sie dann einen der folgenden Aktionen, die Ihre Unternehmensrichtlinien auszurichten:

-   Nicht alle Access zulassen
-   Sperren des Zugriffs auf HBI und MBI-Ressourcen
-   Legen Sie das Gerät in einer Überwachungsliste das Gerät zum potenziellen Risiken besser überwachen.
-   Auslösen einer Maßnahme, wie beispielsweise informiert das Team technischen Support zu wenden Sie sich an den Besitzer das Problem zu untersuchen.

**CodeIntegrityRevListVersion** Dieses Attribut gibt die Version des Codes, die Prüfung der Datenintegrität während der Startsequenz ausgeführt wird. Verwendung dieses Attributs helfen Ihnen bei erkennen, ob das Gerät die neueste Version des Codes ausgeführt wird, die Prüfung der Datenintegrität, ausgeführt wird oder wenn es für Sicherheitsrisiken (gesperrt) verfügbar gemacht wird und eine entsprechende Richtlinienaktion zu erzwingen.

Wenn CodeIntegrityRevListVersion = \[CurrentVersion\], klicken Sie dann auf Zugriff gewähren.

Wenn CodeIntegrityRevListVersion! = \[CurrentVersion\], führen Sie dann einen der folgenden Aktionen, die Ihre Unternehmensrichtlinien auszurichten:

-   Nicht alle Access zulassen
-   Sperren des Zugriffs auf HBI und MBI-Ressourcen
-   Legen Sie das Gerät in einer Überwachungsliste das Gerät zum potenziellen Risiken besser überwachen.
-   Auslösen einer Maßnahme, wie beispielsweise darüber informiert, wenden Sie sich an den Besitzer des Supportteams das Problem zu untersuchen.

**CIPolicyHash** Dieses Attribut gibt die Integrität des Codes-Richtlinie, die die Sicherheit der Boot-Umgebung gesteuert wird.

CIPolicyHash ist nicht vorhanden oder ist ein Wert akzeptiert (White), lassen Sie Zugriff zu.

Wenn CIPolicyHash vorhanden ist, und es kein Wert White ist, führen Sie dann einen der folgenden Aktionen, die mit Ihrer Unternehmensrichtlinien ausrichten:

-   Nicht alle Access zulassen
-   Legen Sie das Gerät in einer Überwachungsliste das Gerät zum potenziellen Risiken besser überwachen.

**SBCPPolicyHash** SBCPPolicyHash ist der Hash von einem benutzerdefinierten Secure Boot Konfiguration Richtlinie (SBCP).

Wenn ein Gerät die Standardrichtlinie verwendet wird (die in Bootmgr eingebettet ist) wird keine Hash hinzugefügt.

Wenn ein Gerät den "Custom" Richtlinie Hash der benutzerdefinierten Richtlinie verwendet, wird es gemessen und die Protokolle TPM hinzugefügt.

Wenn SBCPPolicyHash nicht vorhanden ist oder ein Wert akzeptiert (White ist), lassen Sie Zugriff zu.

Wenn SBCPPolicyHash vorhanden ist, und es kein Wert White ist, führen Sie dann einen der folgenden Aktionen, die mit Ihrer Unternehmensrichtlinien ausrichten:

-   Nicht alle Access zulassen
-   Legen Sie das Gerät in einer Überwachungsliste das Gerät zum potenziellen Risiken besser überwachen.

**PCR0** Die Messung, die in PCR erfasst wird\[0\] in der Regel eine konsistente Ansicht der Host-Plattform zwischen Boot Zyklen darstellt. Sie enthält eine Messung der Komponenten, die vom Hersteller Plattform Host bereitgestellt werden.

Enterprise Manager können eine weiße Liste mit vertrauenswürdigen PCR erstellen\[0\] vergleichen, die PCR\[0\] Wert der verwalteten Geräte (der Wert, der überprüft und berichtet von HAS) mit den weißen und stellen Sie eine vertrauensentscheidung basierend auf dem Ergebnis des Vergleichs.

Wenn Ihr Unternehmen keine weiße Liste mit akzeptierten PCR\[0\] Werte, klicken Sie dann keine Aktion durchführen.

Wenn PCR\[0\] gleich einen Wert akzeptierte White und dann Zugriff gewähren.

Wenn PCR\[0\] keine akzeptierten White Wert gleich, dann führen eine der folgenden Aktionen, die Ihre Unternehmensrichtlinien ausgerichtet:

-   Nicht alle Access zulassen
-   Leiten Sie das Gerät ein Umbenennungsrichtlinie Enterprise weiter Überwachen des Geräts Aktivitäten.

## <a name="additional-examples"></a>**Weitere Beispiele**


Es folgen weitere Codebeispiele unterstützen Sie bei der Integration von Bescheinigung in Ihrem Unternehmen.

## <a name="health-certificate-request"></a>Zertifikatanforderung Integrität


``` syntax
<HealthCertificateRequest ProtocolVersion="1" xmlns="http://schemas.microsoft.com/windows/security/healthcertificate/request/v1">
  <Claims>AAECAwQFBgcICQoLDA0ODw==</Claims>
  <AIKCertificate>AAECAwQFBgcICQoLDA0ODw==</AIKCertificate>
</HealthCertificateRequest>
```

## <a name="health-certificate-response"></a>Integrität Zertifikats Antwort


``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema id="HealthCertificateResponse"
           xmlns="http://schemas.microsoft.com/windows/security/healthcertificate/response/v1"
xmlns:xs="http://www.w3.org/2001/XMLSchema"           targetNamespace="http://schemas.microsoft.com/windows/security/healthcertificate/response/v1"
elementFormDefault="qualified">

    <xs:element name="HealthCertificateResponse" type="HealthCertificateResponse_T"/>

    <xs:complexType name="ResponseCommon_T">
        <xs:attribute name="ErrorCode" type="xs:int" use="required"/>
        <xs:attribute name="ErrorMessage" type="xs:string" use="required"/>
    </xs:complexType>

    <xs:group name="HealthCertificateResponseData">
        <xs:annotation>
            <xs:documentation>Health certificate response data</xs:documentation>
        </xs:annotation>
        <xs:sequence>
            <xs:element name="HealthCertificateBlob"  minOccurs="1" maxOccurs="1">
                <xs:annotation>
                    <xs:documentation>
                      The base 64 encoded Health Certificate blob.
                    </xs:documentation>
                </xs:annotation>
                <xs:simpleType>
                    <xs:restriction base="xs:base64Binary">
                        <xs:minLength value="1"/>
                    </xs:restriction>
                </xs:simpleType>
            </xs:element>
        </xs:sequence>
    </xs:group>

    <xs:complexType name="HealthCertificateResponse_T" >
        <xs:complexContent>
            <xs:extension base="ResponseCommon_T">
                <xs:group ref="HealthCertificateResponseData" minOccurs="0"/>
            </xs:extension>
        </xs:complexContent>
    </xs:complexType>
</xs:schema>
```

## <a name="health-certificate-response-example"></a>Integrität Zertifikat antwortbeispiel


``` syntax
<HealthCertificateResponse ErrorCode="1" ErrorMessage="ErrorMessage1" xmlns="http://schemas.microsoft.com/windows/security/healthcertificate/response/v1">
  <HealthCertificateBlob>AAECAwQFBgcICQoLDA0ODw==</HealthCertificateBlob>
</HealthCertificateResponse>
```

## <a name="health-state-validation-request"></a>Anforderung zur Überprüfung des Health Zustand


``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"
xmlns="http://schemas.microsoft.com/windows/security/healthcertificate/validation/request/v1"
targetNamespace="http://schemas.microsoft.com/windows/security/healthcertificate/validation/request/v1"
elementFormDefault="qualified">

  <xs:element name="HealthCertificateValidationRequest"   type="HealthCertificateValidationRequest_T"/>

  <xs:complexType name="HealthCertificateValidationRequest_T">
    <xs:annotation>
      <xs:documentation>A request for Health Certificate validation </xs:documentation>
    </xs:annotation>
    <xs:sequence>
      <xs:element name="Nonce"                    type="xs:hexBinary"/>
      <xs:element name="Claims"                   type="xs:base64Binary"/>
      <xs:element name="HealthCertificateBlob"    type="xs:base64Binary"/>
    </xs:sequence>
    <xs:attribute name="ProtocolVersion" use="required">
      <xs:simpleType>
        <xs:restriction base="xs:int">
          <xs:minInclusive value="1"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:attribute>
  </xs:complexType>
</xs:schema>
```

## <a name="health-state-validation-request-example"></a>Integrität Zustand Validierung anforderungsbeispiel


``` syntax
<HealthCertificateValidationRequest ProtocolVersion="1" xmlns="http://schemas.microsoft.com/windows/security/healthcertificate/validation/request/v1">
  <Nonce>0FB7</Nonce>
  <Claims>AAECAwQFBgcICQoLDA0ODw==</Claims>
  <HealthCertificateBlob>AAECAwQFBgcICQoLDA0ODw==</HealthCertificateBlob>
</HealthCertificateValidationRequest>
```

## <a name="health-state-validation-response"></a>Integrität Zustand Validierung Antwort


``` syntax
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"
           xmlns="http://schemas.microsoft.com/windows/security/healthcertificate/validation/response/v1"
           targetNamespace="http://schemas.microsoft.com/windows/security/healthcertificate/validation/response/v1"
           elementFormDefault="qualified">

    <xs:element name="HealthCertificateValidationResponse" type="HealthCertificateValidationResponse_T"/>

    <xs:complexType name="ResponseCommon_T">
        <xs:attribute name="ErrorCode" type="xs:int" use="required"/>
        <xs:attribute name="ErrorMessage" type="xs:string" use="required"/>
    </xs:complexType>

    <xs:complexType name="HealthCertificatePublicProperties_T">
        <xs:annotation>
            <xs:documentation>Health certificate non machine identifiable properties </xs:documentation>
        </xs:annotation>
        <xs:sequence>
            <xs:element name="Issued"                       type="xs:dateTime"/>
            <xs:element name="ResetCount"                   type="xs:unsignedInt"/>
            <xs:element name="RestartCount"                 type="xs:unsignedInt"/>
            <xs:element name="DEPPolicy"                    type="xs:unsignedInt"/>
            <xs:element name="BitlockerStatus"              type="xs:unsignedInt"/>
            <xs:element name="SecureBootEnabled"            type="Boolean_T"/>
            <xs:element name="BootDebuggingEnabled"         type="Boolean_T"/>
            <xs:element name="OSKernelDebuggingEnabled"     type="Boolean_T"/>
            <xs:element name="CodeIntegrityEnabled"         type="Boolean_T"/>
            <xs:element name="TestSigningEnabled"           type="Boolean_T"/>
            <xs:element name="SafeMode"                     type="Boolean_T"/>
            <xs:element name="WinPE"                        type="Boolean_T"/>
            <xs:element name="ELAMDriverLoaded"             type="Boolean_T"/>
            <xs:element name="VSMEnabled"                   type="Boolean_T"/>
        </xs:sequence>
    </xs:complexType>

    <xs:complexType name="HealthStatusProperties_T">
        <xs:annotation>
            <xs:documentation>Health certificate validation response data</xs:documentation>
        </xs:annotation>
        <xs:sequence>
            <xs:element name="RestartCount"                  type="xs:unsignedInt"/>
        </xs:sequence>
    </xs:complexType>

    <xs:complexType name="HealthCertificateValidationResponse_T" >
        <xs:annotation>
            <xs:documentation>Health certificate validation response </xs:documentation>
        </xs:annotation>
        <xs:complexContent>
            <xs:extension base="ResponseCommon_T">
                <xs:sequence>
                    <!--Optional element, present only when the certificate can be verified and decrypted-->
                    <xs:element name="HealthCertificateProperties"  type="HealthCertificatePublicProperties_T"  minOccurs="0"/>
                    <!--Optional element, present only when the reason for a validation failure is a mismatch between the 
                    current health state and the certificate health state-->
                    <xs:element name="HealthStatusProperties"       type="HealthStatusProperties_T"             minOccurs="0"/>
                </xs:sequence>
            </xs:extension>
        </xs:complexContent>
    </xs:complexType>
```

## <a name="related-topics"></a>Verwandte Themen


[Konfiguration Dienstverweis-Anbieter](configuration-service-provider-reference.md)

 

 






